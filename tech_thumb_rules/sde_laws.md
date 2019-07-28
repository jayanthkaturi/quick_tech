
[Source](https://www.timsommer.be/famous-laws-of-software-development/ "Permalink to Famous laws of Software development")

# Famous laws of Software development

Like any other field, the world of Software Development has some interesting and famous rules, principles and laws. Programmers, developers, managers and architects often use these in conversations, meetings and chats. More than often we tend to nod along, not willing to let our conversation partner know we've actually never heard of these Brook, Moore or Wirth characters.

These laws consist of rules, principles, or famous words from great and inspiring persons in the development world. At the same time they are interesting, funny, worth knowing, and all have great back-stories which are amazing to read.

In this post I am going to share my collection, interpretation and thoughts on the most famous and most used laws in Software Development.

This is kind-off a big post, so I've included an index if you want to skip some:

## Murphy's Law

Probably one of the most famous of all laws, mostly because it is not only applicable to Software Development.

> If something can go wrong, it will.

**First derivation:** If it works, you probably didn't write it.  
**Second derivation:** Cursing is the only language all programmers speak fluently.  
**Conclusion:** A computer will do what you write, not what you want.

Defensive programming, version control, doom scenario's (for those damned zombie-server-attacks), TDD, MDD, etc. are all are good practices for defending against this law.

## Brook's Law

Most developers will -either knowingly or unknowingly- have experience with Brook's law, which states:

> Adding manpower to a late software project makes it later.

If a project is running late, simply adding manpower will most likely have disastrous results. Looking and reviewing the level of programming efficiency, the software methodology, the technical architecture, etc. will almost always have better outcomes. Or not, which probably means Hofstadter's Law is also in play.

## Hofstadter's Law

![hofstader-1][1]

The Hofstadter's law was written by Douglas Hofstadter and named after him.

This law is -off course- not to be confused with Leonard Hofstadter from the Big Bang theory. Even though his quotation will make sense to some you.

The rule states:

> It always takes longer than you expect, even when you take into account Hofstadter's Law.

The "law" is a statement regarding the difficulty of accurately estimating the time it will take to complete tasks of substantial complexity. The recursive nature of the law is a reflection of the widely experienced difficulty of estimating complex tasks despite all best efforts, including knowing that the task is complex.

That's why you must always have a buffer before you give any sort of estimation. If you want to know more on how to provide better estimations, read my post on the subject: [Estimation Wizardry][2].

## Conway's Law

> Any piece of software reflects the organizational structure that produced it.

Or even more clearly:

> Organizations which design systems are constrained to produce designs which are copies of the communication structures of these organizations.

In many organizations teams are divided according to their functional skills. So you'll have teams of front-end developers, backend-developers and database developers. Simply stated, it's hard for someone to change something if the thing he/she wants to change is owned by someone else.

It is much better, and more and more implemented as such, to deploy teams around a bounded context. Architectures such as microservices structure their teams around service boundaries rather than siloed technical architecture partitions.

So, structure teams to look like your target architecture, and it will be easier to achieve it. That's how you defend against Conways's law.

## Postel's Law aka Robustness principle

> Be conservative in what you send, be liberal in what you accept

Jon Postel originally articulated this as a principle for making TCP implementations robust. This principle is also embodied by HTML which many attribute as a cause of its success and failure, depending on who you ask.

In today's highly charged political environment, Postel's law is a uniter.

## Pareto Principle aka The 80-20 rule

> For many phenomena, 80% of consequences stem from 20% of the causes.

This is the principle behind the painful truth that 80% of the bugs in the code arise from 20% of the code.  
Otherwise stated, 80% of the work done in a company is performed by 20% of the staff. The problem is you don't always have a clear idea of which 20%.

## The Peter Principle

A pretty depressing and at times frustrating law, certainly if you happen to have firsthand experience.

> In a hierarchy, every employee tends to rise to his level of incompetence.

Just read Dilbert (or watch The Office) to get some examples of this in action.  
As for Dilbert, this one is far out my favorite!

![dilvert][3]

## Kerchkhoff's Principle

> In cryptography, a system should be secure even if everything about the system, except for a small piece of information - the key - is public knowledge.

This is the main principle underlying public key cryptography.

## Linus's Law

Named after Linus Torvalds, the creator of Linux, this law states:

> Given enough eyeballs, all bugs are shallow.

This law was described using the famous [The Cathedral and the Bazaar][4] essay, explaining the contrast between two different free software development models:

* The Cathedral model, in which source code is available with each software release, but code developed between releases is restricted to an exclusive group of software developers.
* The Bazaar model, in which the code is developed over the **Internet in view of the public**.

The conclusion? The more widely available the source code is for public testing, scrutiny, and experimentation, the more rapidly all forms of bugs will be discovered.

## Moore's Law

> The power of computers per unit cost doubles every 24 month.

The most popular version states:

> The number of transistors on an integrated circuit will double in about 18 months.

Or

> The processing speed of computers will double every two years!

![moore][5]

## Wirth's law

> Software gets slower faster than hardware gets faster.

Take that Moore's Law!

## Ninety-ninety rule

> The first 90% of the code takes 10% of the time. The remaining 10% takes the other 90% of the time

So true. Anyone who does not agree with this?

## Knuth's optimization principle

> Premature optimization is the root of all evil.

![optimization][6]

First you write code, then you identify bottlenecks, then you fix!

  

## Norvig's Law

> Any technology that surpasses 50% penetration will never double again (in any number of months).

## Conclusion

I love these 'laws' as they each have their own story, their own background. And as a consultant or architect you have to familiarize yourself with them. So for me, and possibly for you, I know have a list of the most used and most famous laws in Software Development!

Did I miss your favorite law? Do (or don't) you agree with each law, or have any (funny) experience with one of them? What is your favorite? Let me know using the comment section!

[1]: https://www.timsommer.be/content/images/2017/12/hofstader-1.jpg
[2]: https://www.timsommer.be/estimation-wizardry
[3]: https://www.timsommer.be/content/images/2017/12/dilvert.jpg
[4]: https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar
[5]: https://www.timsommer.be/content/images/2017/12/moore.jpg
[6]: https://www.timsommer.be/content/images/2017/12/optimization.png

  
