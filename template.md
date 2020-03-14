## Bash (Bourne Again Shell)

- History of the language: who/when invented it, which languages influenced it, etc.
- Why was it invented
- When/why shall we use it

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
