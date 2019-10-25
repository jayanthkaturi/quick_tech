<div class="skip">[Skip to Main Content](#main-content)</div>

<div class="wrapper">

<header class="cf">[![Computer Hope](/cdn/computer-hope.jpg)](/)

<div itemscope="" itemtype="https://schema.org/SiteNavigationElement">

<form action="https://www.computerhope.com/cgi-bin/search.cgi" method="post"><input class="sbar" name="q" title="Search" type="text" accesskey="s"> <button type="Submit">Search</button></form>

*   [Help](/oh.htm "Questions and answers, troubleshooting, and help")
*   [Tips](/tips/ "Computer tips and tricks")
*   [Dictionary](/jargon.htm "Computer terms, jargon, and glossary")
*   [History](/history/ "Computer timeline, events, and biographies")
*   [Forums](/forum/ "Computer Hope forums and community")
*   [Contact](/contact/ "Contact Computer Hope or other computer companies")

</div>

</header>

<div class="container ad"><script>(adsbygoogle = window.adsbygoogle || []).push({});</script></div>

<div class="container">

1.  [<span itemprop="name">Home</span>](/)<meta content="1" itemprop="position">
2.  [<span itemprop="name">Help</span>](/oh.htm)<meta content="2" itemprop="position">
3.  [<span itemprop="name">Linux</span>](/unix.htm)<meta content="3" itemprop="position">

</div>

<div class="container content" id="main-content">

<article>

# Linux umask command

<div class="updated">Updated: <span itemprop="dateModified" content="2019-05-04">05/04/2019</span> by <span itemprop="author publisher creator" itemscope="" itemtype="https://schema.org/Organization"><span itemprop="name">Computer Hope</span></span></div>

![umask command](/cdn/linux/umask.gif)

On [Unix-like](/jargon/u/unix-like.htm) operating systems, the **umask** command returns, or sets, the value of the system's file mode creation mask.

This document covers the [Linux](/jargon/l/linux.htm) version of **umask**.

<div class="pagenav contents">

*   [Description](#desc)
*   [Syntax](#syntax)
*   [Examples](#examples)
*   [Related commands](#related)
*   [Linux commands help](/unix.htm)

</div>

## Description

On [Linux](/jargon/l/linux.htm) and other [Unix](/jargon/u/unix.htm)-like [operating systems](/os.htm), new [files](/jargon/f/file.htm) are created with a default set of [permissions](/jargon/p/permissi.htm). Specifically, a new file's permissions may be _restricted_ in a specific way by applying a permissions "mask" called the **umask**. The **umask** command is used to set this mask, or to show you its current value.

## Syntax

<pre class="tcy tab">umask [-S] [_mask_]</pre>

## Options

<table class="mtable3 tab">

<tbody>

<tr class="tcw">

<td>**-S**</td>

<td>Accept a symbolic representation of a _mask_, or return one.</td>

</tr>

<tr class="tcw">

<td>_mask_</td>

<td>If a valid _mask_ is specified, the umask is set to this value. If no _mask_ is specified, the current umask value is returned.</td>

</tr>

</tbody>

</table>

## What are permissions, and how do they work?

As you may know, each file on your system has associated with it a set of _permissions_ that are used to protect files: a file's permissions determine which users may access that file, and what type of access they have to it.

There are three general classes of users:

*   The user who [owns](/jargon/o/owner.htm) the file ("**User**").
*   Users belonging to the file's defined ownership group ("**Group**").
*   Everyone else ("**Other**").

In turn, for each of these classes of user, there are three types of file access:

*   The ability to look at the contents of the file ("**Read**").
*   The ability to change the contents of the file ("**Write**").
*   The ability to run the contents of the file as a program on the system ("**Execute**").

So, for each of the three classes of user, there are three types of access. Taken together, this information makes up the file's _permissions_.

## How are permissions represented?

There are two ways to represent a file's permissions: symbolically (using symbols like "**r**" for read, "**w**" for write, and "**x**" for execute) or with an [octal](/jargon/o/octal.htm) numeric value.

For example, when you list the contents of a directory at the [command line](/jargon/c/commandi.htm) using the [ls](/unix/uls.htm) command as follows:

<pre class="tab tcy">ls -l </pre>

you will see (among other information) the file permission information for each file. Here, it is represented _symbolically_, which will look like the following example:

<pre class="tab">-rwxr-xr-- </pre>

There are ten symbols here. The first dash ("**-**") means that this is a "regular" file, in other words, not a directory (or a device, or any other special kind of file). The remaining nine symbols represent the permissions: **rwxr-xr--**. These nine symbols are actually three sets of three symbols each, and represent the respective specific permissions, from left to right:

<table class="mtable3 tab">

<tbody>

<tr class="tcy">

<th>symbols</th>

<th>meaning</th>

</tr>

<tr class="tcw">

<td>**rwx**</td>

<td>**the file's owner** may **read**, **write**, or **execute** this file as a process on the system.</td>

</tr>

<tr class="tcw">

<td>**r-x**</td>

<td>anyone in **the file's group** may **read** or **execute** this file, but not write to it.</td>

</tr>

<tr class="tcw">

<td>**r--**</td>

<td>**anyone at all** may **read** this file, but not write to it or execute its contents as a process.</td>

</tr>

</tbody>

</table>

## Specifying the file creation mask using symbols

The general symbolic form of a mask is as follows:

<pre class="tcy tab">[_user class symbol(s)_][_permissions operator_][_permission symbol(s)_][**,**]...</pre>

_permission symbol_ is any combination of **r** (read), **w** (write), or **x** (execute), as described above.

_user class symbol_ may be one or more of the following:

<table class="mtable3 tab">

<tbody>

<tr class="tcw">

<td>**u**</td>

<td>User (the owner of the file).</td>

</tr>

<tr class="tcw">

<td>**g**</td>

<td>Group (any member of the file's defined group).</td>

</tr>

<tr class="tcw">

<td>**o**</td>

<td>Other (anyone else).</td>

</tr>

<tr class="tcw">

<td>**a**</td>

<td>All (equivalent to **ugo**).</td>

</tr>

</tbody>

</table>

_permissions operator_ may be one of the following:

<table class="mtable3 tab">

<tbody>

<tr class="tcw">

<td>**+**</td>

<td>allow the specified file permissions to be enabled for the specified user classes (permissions that are not specified are unchanged in the mask).</td>

</tr>

<tr class="tcw">

<td>**-**</td>

<td>prohibit the specified file permissions from being enabled for the specified user classes (permissions that are not specified are unchanged in the mask).</td>

</tr>

<tr class="tcw">

<td>**=**</td>

<td>allow the specified file permissions to be enabled for the specified user classes (permissions not specified will be prohibited by the mask during file creation).</td>

</tr>

</tbody>

</table>

So, for example, the following **umask** command:

<pre class="tcy tab">umask u+w</pre>

sets the mask so that when files are created, they will have permissions which allow write permission for the user (file owner). The rest of the file's permissions would be unchanged from the operating system default.

Multiple changes can be specified by separating multiple sets of symbolic notation with commas (but not spaces!). For example:

<pre class="tcy tab">umask u-x,g=r,o+w</pre>

This command will set the mask so that when subsequent files are created, they will have permissions that:

1.  prohibit the execute permission from being set for the file's owner (user), while leaving the rest of the owner permissions unchanged;
2.  enable read permission for the group, while prohibiting write and execute permission for the group;
3.  enable write permission for others, while leaving the rest of the other permissions unchanged.

Note that if you use the equals operator ("**=**"), any permissions not specified will be specifically prohibited. For example, the command

<pre class="tcy tab">umask a=</pre>

Will set the file creation mask so that new files are inaccessible to everyone.

## Specifying the file creation mask using numeric representation

The file creation mask can also be represented _numerically_, using octal values (the digits from 0 to 7). When using octal numeric representation, certain numbers represent certain permissions, and these numbers are added or subtracted from each other to represent the final, combined permissions value. Specifically, the numbers **1**, **2**, and **4** represent the following permissions:

<table class="mtable3 tab">

<tbody>

<tr class="tcy">

<th>number</th>

<th>permission</th>

</tr>

<tr class="tcw">

<td>**4**</td>

<td>read</td>

</tr>

<tr class="tcw">

<td>**2**</td>

<td>write</td>

</tr>

<tr class="tcw">

<td>**1**</td>

<td>execute</td>

</tr>

</tbody>

</table>

These numbers are used because any combination of these three numbers will be unique. The following table illustrates their unique combinations:

<table class="mtable3 tab">

<tbody>

<tr class="tcy">

<th>read value +</th>

<th>write value +</th>

<th>execute value =</th>

<th>combined value:</th>

<th>symbolic equivalent:</th>

</tr>

<tr class="tcw">

<td>0</td>

<td>0</td>

<td>0</td>

<td>**0**</td>

<td></td>

</tr>

<tr class="tcw">

<td>0</td>

<td>0</td>

<td>**1**</td>

<td>**1**</td>

<td>**x**</td>

</tr>

<tr class="tcw">

<td>0</td>

<td>**2**</td>

<td>0</td>

<td>**2**</td>

<td>**w**</td>

</tr>

<tr class="tcw">

<td>0</td>

<td>**2**</td>

<td>**1**</td>

<td>**3**</td>

<td>**wx**</td>

</tr>

<tr class="tcw">

<td>**4**</td>

<td>0</td>

<td>0</td>

<td>**4**</td>

<td>**r**</td>

</tr>

<tr class="tcw">

<td>**4**</td>

<td>0</td>

<td>**1**</td>

<td>**5**</td>

<td>**rx**</td>

</tr>

<tr class="tcw">

<td>**4**</td>

<td>**2**</td>

<td>0</td>

<td>**6**</td>

<td>**rw**</td>

</tr>

<tr class="tcw">

<td>**4**</td>

<td>**2**</td>

<td>**1**</td>

<td>**7**</td>

<td>**rwx**</td>

</tr>

</tbody>

</table>

For each class of user, one digit can be used to represent their permissions; using the example above, we could represent the symbolic permission of **rwxr-xr--** using the three-digit octal number **754**. The order of the digits is always the same: **User**, **Group**, **Other**.

## The other permission digit

In octal representations of file permissions, there are actually four digits. The three important digits we've discussed are the last three digits. The first digit is a special file permission indicator, and for the purposes of this discussion can be considered always to be zero. So from here on out, when we discuss file permission **777**, it may also be referred to as **0777**.

## So how does the umask actually work?

The **umask** _masks_ permissions by restricting them by a certain value.

Essentially, each digit of the umask is "subtracted" from the OS's default value to arrive at the default value that you define. It's not really subtraction; technically, the mask is negated (its [bitwise](/jargon/b/bitwoper.htm) compliment is taken) and this value is then applied to the default permissions using a [logical AND](/jargon/b/boolean.htm) operation. The result is that the umask tells the operating system which permission bits to "turn off" when it creates a file.

In Linux, the default permissions value is **666** for a regular file, and **777** for a directory. When creating a new file or directory, the [kernel](/jargon/k/kernel.htm) takes this default value, "subtracts" the umask value, and gives the new files the resulting permissions.

This table shows how each digit of the **umask** value affects new file and directory permissions:

<table class="mtable3 tab">

<tbody>

<tr class="tcy">

<th>umask digit</th>

<th>default file permissions</th>

<th>default directory permissions</th>

</tr>

<tr class="tcw">

<td>**0**</td>

<td>rw</td>

<td>rwx</td>

</tr>

<tr class="tcw">

<td>**1**</td>

<td>rw</td>

<td>rw</td>

</tr>

<tr class="tcw">

<td>**2**</td>

<td>r</td>

<td>rx</td>

</tr>

<tr class="tcw">

<td>**3**</td>

<td>r</td>

<td>r</td>

</tr>

<tr class="tcw">

<td>**4**</td>

<td>w</td>

<td>wx</td>

</tr>

<tr class="tcw">

<td>**5**</td>

<td>w</td>

<td>w</td>

</tr>

<tr class="tcw">

<td>**6**</td>

<td>x</td>

<td>x</td>

</tr>

<tr class="tcw">

<td>**7**</td>

<td>(no permission allowed)</td>

<td>(no permission allowed)</td>

</tr>

</tbody>

</table>

So if our **umask** value is **022**, then any new files will, by default, have the permissions **644** (666 - 022). Likewise, any new directories will, by default, be created with the permissions **755** (777 - 022).

## Examples

To view your system's current **umask** value, enter the command:

<pre class="tcy tab">umask</pre>

which will return your system's umask as a four-digit octal number, for example:

<pre class="tab">0002</pre>

Again, the first zero is a special permission digit and can be ignored; for our purposes, **0002** is the same as **002**.

To view this as a symbolic representation, use the **-S** flag:

<pre class="tcy tab">umask -S</pre>

Which will return the same value symbolically, for example:

<pre class="tab">u=rwx,g=rwx,o=rx</pre>

where **u** stands for **user**, **g** stands for **group**, and **o** stands for **other**. This is telling us the So if we create a new file, it will have the default permissions **664**, which is **666** (the default permissions for files) masked by **002** (our umask value).

Let's test this by creating a new file with the [touch](/unix/utouch.htm) command:

<pre class="tcy tab">touch testfile</pre>

And now let's get a directory listing for that file:

<pre class="tcy tab">ls -l testfile</pre>

<pre class="tab">-rw-rw-r-- 1 myusername myusername 0 Jan 7 14:29 testfile</pre>

As expected, the new file has permissions **-rw-rw-r--**, or **0664**: The owner and group may read or write the file, and others may only read it.

Now let's change the umask. To set a umask of **022**, use the command:

<pre class="tcy tab">umask 022</pre>

This is the same as running **umask 0022**; if you specify only three digits, the first digit will be assumed to be zero. Let's verify that the change took place:

<pre class="tcy tab">umask</pre>

<pre class="tab">0022</pre>

And now let's create a new file:

<pre class="tcy tab">touch testfile2</pre>

And now let's view its directory listing, along with the first file we created, using the asterisk [wildcard](/jargon/w/wildcard.htm) ("*****") to view all files whose name start with "**testfile**":

<pre class="tcy tab">ls -l testfile*</pre>

<pre class="tab">-rw-rw-r-- 1 myusername myusername 0 Jan  7 14:29 testfile
-rw-r--r-- 1 myusername myusername 0 Jan  7 14:39 testfile2</pre>

As you can see, **testfile2** has the permissions **644**.

Here are some other example **umask** commands:

<pre class="tcy tab">umask a+r</pre>

Sets the mask so that new files will allow all users to read them; other permissions will be unchanged from the default.

umask a-x

Sets the mask so that new files will not initially be executable by any user; other default permissions unchanged from defaults.

umask u=rw,go=

Sets the mask so that new files will be readable and writable by the user who owns the file, but may not be executed; group members and others will have no permissions to access the file.

<pre class="tcy tab">umask 777</pre>

Make new files inaccessible to everyone - no one can read, write, or execute them.

<pre class="tcy tab">umask 000</pre>

Make new files completely accessible (read, write, and execute) to absolutely everyone. However, this is a bad idea. Don't do this.

## Related commands

[**chmod**](/unix/uchmod.htm) — Change the permissions of files or directories.  
[**csh**](/unix/ucsh.htm) — The C shell command interpreter.  
[**ksh**](/unix/uksh.htm) — The Korn shell command interpreter.  
[**sh**](/unix/ush.htm) — The Bourne shell command interpreter.

</article>

<div class="bottomad"><script>(adsbygoogle = window.adsbygoogle || []).push({});</script>

<div class="related"><script>(adsbygoogle = window.adsbygoogle || []).push({});</script></div>

</div>

<div class="cf" id="meta_wrap">

*   <span class="nolink">Was this page useful?</span> [Yes](/cgi-bin/feedback.cgi?yes) [No](/cgi-bin/feedback.cgi?no)
*   *   [Feedback](/feedback/ "Give us your feedback about this page")
    *   [E-mail](/contact/ "E-mail Computer Hope")
    *   [Share](/share/ "Share this page with friends and social networks")
    *   [Print](# "Print a copy of this page")

</div>

</div>

<footer>

<form action="https://www.computerhope.com/cgi-bin/search.cgi" method="post" class="cf"><input class="sbar" name="q" title="Search" type="text"> <button type="Submit">Search</button></form>

*   1.  ##### Recently added pages

    7.  [View all recent updates](/whatnew.htm)
*   1.  ##### Useful links

    2.  [About Computer Hope](/more.htm)
    3.  [Site Map](/sindex.htm)
    4.  [Forum](/forum/)
    5.  [Contact Us](/contact/)
    6.  [How to Help](/issues/ch000586.htm)
    7.  [Top 10 pages](/chtop10.htm)
*   1.  ##### Follow us

    2.  [Facebook](https://www.facebook.com/computerhope/)
    3.  [Twitter](https://twitter.com/computerhope/)
    4.  [Pinterest](https://www.pinterest.com/computerhope/)
    5.  [YouTube](https://www.youtube.com/user/Computerhope/)
    6.  [RSS](/rss.htm)

<div class="copyright">© 2019 Computer Hope  
[Legal Disclaimer - Privacy Statement](/legal.htm)</div>

</footer>

</div>
