## Bash (Bourne Again Shell)

#### Name, Author and History of the Language
   Bash or GNU Bash is a Unix shell and command language written by Brian Fox, who is a computer programmer 
and entrepreneur, in 1989.  When Richard Stallman who is the founder of Free Software Foundation became 
displeased to the prior developer than Brian, he started to coding Bash under the GNU Project in 1988. Its name is
an acronym for Bourne-Again-Shell and refers to the 'Bourne Shell' developed by Stephen Bourne.Some of the purpose
of Bourne Shell were allowing shell scripts to be used as filters,controlling over all input/output file descriptors.
rationalizing and generalizing string quoting mechanism etc. when it was distributed for UNIX version 7. in 1979.
 
 
#### Why was it invented
   Bourne shell was a new Unix shell written by Stephen Bourne at Bell Labs(Bell Telephone Laboratories).It was 
a replacement for the Thompson hell. Before Bourne Shell family(Early Shells), there were different Unix Shells 
such as Thompson shell, Multics shell etc.These shells were not developed enough to meet the needs. Bourne shell  
created with many features like providing a set of built-in commands, allowing both synchronous and asynchronous
execution of commands,provides flow control constructs, quotation facilities, and function etc. Until 1989 it was
used but at then it was replaced by a more advanced version called 'Bash' which was influenced by Bourne shell.
   
   
#### When/why shall we use Bash
   To understand the importance of Bash, we need to understand what is a shell or specifically  what is the 
UNIX shell since Bash is the default shell for most of the Linux installations.
   A shell is simply a macro processor that executes commands. The term macro processor means functionality 
where text and symbols are expanded to create larger expressions.
   A Unix shell is both a command interpreter and a programming language. As a command interpreter, the shell
provides the user interface to the rich set of GNU utilities. that provides a command line interface(CLI) for 
Unix-like operating systems. The main purpose of a UNIX shell is to allow users to interact effectively with 
the system through the command line 
   The terminal is an important component of any useful operating system. It is one of the most important applications
on Mac and Linux. The terminal provides an efficient interface to better access the real power of a computer than 
any graphical interface and when we open terminal we are presented by shell and in Linux and Mac the Shell is 
Bash. We can also use a version of Bash in Windows, even though it is not preinstalled.
   Bash is also a scripting language, meaning we can create scripts that can run multiple commands, support control 
structures, variables, and much more.
   There are many reason to why should we use Bash as both scripting language or interpreter. For example, it's the 
most efficient shell scripting language, we can automate the frequently performed operations, it's portable and
very easy to use. We can use bash for doing amazing works but should be careful and be aware of the power of bash. 
Because when using Bash we are executing the power you have over the computer, and carelessly written codes may 
cause undesirable results


#### How to setup an environment to use it in different platforms
Bash is preinstalled in nearly every Unix system, including BSD-derivatives,
Linux-derivatives and MacOS. On the other hand, Windows recently added a feature
called **Linux Subsystem for Windows**, which is a compatibility layer for running
native Linux apps under Windows 10, and that includes Bash. By activating this
feature, Bash can be accessed like a normal app in Windows.

#### Example codes
By the design, Bash is heavly dependent on other programs and is used for
running and connecting these programs in a programming manner. That's what it's
all about. Here are some examples:

Logging in to a server:
```bash
curl -v -X POST --data "email=example@mail.com&password=123456789" http://exampleserver.com/rest/login
```

Compiling an application:
```bash
 cd "${srcdir}/apr-util-${pkgver}"
 ./configure --prefix=/usr --with-apr=/usr --with-ldap --with-crypto \
   --with-gdbm=/usr --with-sqlite3=/usr --with-nss=/usr --with-odbc=/usr \
   --with-berkeley-db=/usr --with-pgsql=/usr --with-mysql=/usr --with-oracle=/usr \
   --with-openssl=/usr
 make
```

When your task is a bit more complex you can use, bash's prograaming features.

A simple if statement:
```bash
 [[ $silent ]] && [[ $interactive ]]; then
   echo -e "\033[91mOptions --silent and --interactive are mutually exclusive. Please choose one or the other.\033
   exit 1;
 fi
```

What's knows as a switch statement. Here, the first case is when string starts with darwin 
and followed by anything. This is **not** regex, it's something called pattern matching
and is unique to bash. A regex equivalent of this would be darwin.*:
```bash
 case $OSTYPE in
   darwin*)
     CONFIG_FILE=.bash_profile
     ;;
   *)
     CONFIG_FILE=.bashrc
     ;;
 esac
```

A while loop to prompt user to get an action:

```bash
while true
    do
      just_the_name="${file_name%%.*}"
      read -e -n 1 -p "Would you like to enable the $just_the_name $file_type? [y/N] " RESP
      case $RESP in
      [yY])
        $enable_func $just_the_name
        break
        ;;
      [nN]|"")
        break
        ;;
      *)
        echo -e "\033[91mPlease choose y or n.\033[m"
        ;;
      esac
done
```

#### Things that are specific to this language?
Bash, in and of itself, is a very specific languague. It is a **shell** language and
it's in the core of the UNIX system (or it was, when it all started) therefore it implements
its philosophy and its design.

##### Executing programs
To execute a program in bash, all you have to do is to write its executable name, and bash
will do the rest. Unlike a regular programming language, which in that case, you'll have to
create a subprocess and execute that program in the way that it demands and get the output somehow.

##### $PATH variable
PATH variable is what makes possiible to execute programs in the way bash does. When you write an
executable name, bash will look for that in file, in places that are declared in bash.

##### Pipe ( | )
Pipe is a very unique and special operator in bash, and it is just as important. UNIX philosophy mainly
demands that in a system there should be small parts that do only one thing and do it good, alongside with that
there should be connections in this system for these small parts to work together. Pipe is the physical 
part of this idea, it is very common and very useful.

What it does is basically taking the output from one program and send it as input to another one. It's just
simple as that, yet so powerful.

##### Redrirection operators (> >> <)
These are some other operators for redirectin input in a similar manner.

- **>** redirects the output of the program to a file.
- **>>** appends the output of the program to a file.
- **<** redirects the contents of the file to a program as input.
