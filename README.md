# looptimeout


## General information

This repository contains a shell script named `looptimeout` that repeats the
following sequence indefinitely (or until the user kills it):

* Launch a command COMMAND (possibly with arguments), with the standard output
  redirected to a file;

* Terminate the command after a while (DURATION) if it's still running.

The name of the file used for redirection is changed on each sequence iteration
(a suffix (iteration number) is added to the name FILE provided by the user on
the command line).

When the number of generated files reaches a limit, the oldest one is deleted
on each iteration.

The script relies on command `timeout` to kill COMMAND. `timeout` is probably
available on your system. For example, on a [Debian
GNU/Linux](https://www.debian.org) system, `timeout` is provided by package
"coreutils".

`looptimeout` has been tested on a Debian GNU/Linux system, with `dash` as
`/bin/sh`.


## Documentation for script looptimeout

> Usage:
>
>     looptimeout DURATION FILE LIMIT COMMAND [ARG ...]
>
>     looptimeout -h|--help
>
> Description:
>
>     Run command "timeout DURATION COMMAND ARG > NUMBERED_FILE" in a loop.
>
>     NUMBERED_FILE is argument FILE suffixed with loop iteration number (four
>     digits, left padded with zeros). Iteration number starts at 0 and is
>     modulo 10000.
>
>     LIMIT is the maximum number of generated files. If it's lower than 1,
>     then it is substituted with 1. If it's greater than 10000 then it is
>     substituted with 10000. If the maximum number of generated files is
>     reached, then timeout deletes the oldest one on each loop iteration.
>
> Options:
>
>     -h, --help
>         Display this documentation and exit.


## Author

[Thierry Rascle](mailto:thierr26@free.fr)


## License

This project is licensed under the [Unlicense](https://unlicense.org). For more
information, please refer to the [LICENSE](LICENSE) file.
