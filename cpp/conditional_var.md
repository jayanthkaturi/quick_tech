
[Source](http://jakascorner.com/blog/2016/01/condition-variable.html "Permalink to Condition variable")

# Condition variable

Another big topic of concurrent programming is how to synchronize the threads between each other. There are several techniques which allow us to do the synchronization. Today, we will study synchronization mechanism called **a condition variable**.

The condition variable is associated with an event or condition. Roughly speaking, a thread is doing some of the following activities

* changing the condition and notifying other threads about it,
* waiting for the condition to be satisfied.

Let's clarify the abstractions above with an example.

## Mother and son with the laundry

There is a family with a mother and a son. The son is playing basketball and he is sweating, because he is playing hard. Afterwards, he asks the mother to do the laundry for him. She is nice and does it. The son is happy, because he has fresh shirt and shorts. (Any connection with the author of this article is merely apparent :-).)

We will put this short story into the code. There are two processes:

* the mother is doing the laundry,
* the son is playing basketball and outsourcing the laundry to his mother.

These two processes will run in separate threads. There is a communication/synchronization between them which is done via a condition variable.

Let's begin with the code. We start with include statements and global variables. We would avoid the global variables in serious code and use classes with data members. But it is OK to use global variables for this demonstration.
    
    
    #include 
    #include 
    
    #include 
    #include 
    #include 
    
    
    enum class Laundry {CLEAN, DIRTY};
    
    std::mutex MUT;
    Laundry SONS_LAUNDRY = Laundry::CLEAN;
    std::condition_variable CV;
    
    bool is_laundry_clean()
    {
        return SONS_LAUNDRY == Laundry::CLEAN;
    }
    
    bool is_laundry_dirty()
    {
        return SONS_LAUNDRY == Laundry::DIRTY;
    }

Because we will use a condition variable, we need to include `` header. The condition variable `CV`is associated with two things:

* The mutex `MUT`, which helps with the synchronization.
* The enum `SONS_LAUNDRY`, which describes the state of the laundry.

The next two functions check the state of the laundry and return true if the laundry is clean or dirty.

The next section of code describes the behavior of the mother.
    
    
    void clean_laundry()
    {
        std::unique_lock< std::mutex > lock(MUT);
        CV.wait(lock, is_laundry_dirty);
    
        std::cout << "Doing the son's laundry." << std::endl;
        SONS_LAUNDRY = Laundry::CLEAN;
        std::cout << "The laundry is clean." << std::endl;
    
        lock.unlock();
        CV.notify_one();
    }

The function acquires an unique lock on the mutex. Then it calls a `wait()` member function, of the `CV` object, passing the lock and the function `is_laundry_dirty`. The `wait()` function checks the condition, by calling `is_laundry_dirty()`. There are two possibilities:

* If the condition is satisfied – the laundry is dirty – `wait()` returns and the program continues.
* If the condition is not satisfied – the laundry is clean – `wait()` unlocks the mutex and puts the thread in a waiting state. The thread stops waiting when a `notify_one()` member function of the condition variable is called. When the thread stops waiting, it reacquires the lock of the mutex and checks the condition again, by calling `is_laundry_dirty()`. The `wait()` returns only if `is_laundry_dirty()` returns `true`, otherwise `wait()` starts waiting again.

We must use a `std::unique_lock`, because `wait()` unlocks the mutex and locks it again. This is not possible with the `std::lock_guard`.

Once the condition is satisfied, we change the `SONS_LAUNDRY` to `Loundry::CLEAN`. (The mother does the laundry.) Afterwards, the function unlocks the mutex and notifies the condition variable by calling `notify_one()`. The notification is aiming the other thread (the son).

The next section of code describes the behavior of the son.
    
    
    void play_around()
    {
        std::cout << "Playing basketball and sweating." << std::endl;
        {
            std::lock_guard< std::mutex > lock(MUT);
            SONS_LAUNDRY = Loundry::DIRTY;
        }
    
        std::cout << "Asking mother to do the laundry." << std::endl;
        CV.notify_one();
    
        // waiting
        {
            std::unique_lock< std::mutex > lock(MUT);
            CV.wait(lock, is_laundry_clean);
        }
    
        std::cout << "Yea, I have a clean laundry! Thank you mum!" << std::endl;
    }

The function prints some information and then locks the mutex. The mutex is automatically unlocked, after we set the `SONS_LAUNDRY` to dirty, because we put the lock guard object inside a new scope.

Then, the function notifies the waiting thread (the mother).

Afterwards, we start waiting for the clean laundry. The code is again inside a new scope and it is similar to the beginning of the `clean_laundry()` function. The difference is that we are waiting for the clean laundry and not for the dirty one.

At the end, the printing indicates that the mother cleaned the laundry.

The main function is simple. It creates two threads: `mother` and `son` with functions `clean_laundry` and `play_around`, respectively.
    
    
    int main()
    {
    
        std::thread mother(clean_laundry);
        std::thread son(play_around);
    
        mother.join();
        son.join();
    }

You can look at the entire source code [here][1].

## Running the example

The code might be a bit complicated at first sight. The figure can help us understand the timeline of the execution of the program.

![Condition variable with mother and son.][2]

The red color represents the `mother`'s thread, the blue color represents the `son`'s thread and the black color in the middle represents condition variable.

The `mother` starts with waiting for the dirty laundry, while the `son` is playing basketball.

Then, the `son`, via the condition variable, asks the `mother` to do the laundry for him. The `son` is then waiting for the clean laundry while the `mother` does the laundry.

Finally, the `mother`, via the condition variable, informs the `son` about the clean laundry and the `son` lives happily ever after.

We can also verify the code by running it and looking at the output.
    
    
    $ ./conditionVariable
    Playing basketball and sweating.
    Asking mother to do the laundry.
    Doing the son's laundry.
    The laundry is clean.
    Yea, I have a clean laundry! Thank you mum!

## Summary

We learned one of the techniques for thread synchronization.

Links:

[1]: https://github.com/jakaspeh/concurrency/blob/master/conditionVariable.cpp
[2]: http://jakascorner.com/pics/mother_son_condition_variable.png

  
