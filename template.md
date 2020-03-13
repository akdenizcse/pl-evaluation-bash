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

A while loop to prompt user about an action:

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
