---
title: Basic Concepts
date: 2018-09-15 07:42:34
slug: basic-concepts
---

## Creating a Command
Quo is based on declaring commands through transform.
A function order for a function to become a Quo command-line tool, you have to transform it through `quo.command()`. Transoforming a function turns it into a callable script:
```Console
import quo

@quo.command()
def hello():
    quo.echo('Hello World!')
    
// This converts the function into a Command which then can be invoked:

if __name__ == '__main__':
    hello()
```
```Python
$ python hello.py
Hello World!
// And the corresponding help page:

$ python hello.py --help
Usage: hello.py [OPTIONS]

Options:
  --help  Show this message and exit.
```
  
## Echoing
The `echo()` function applies some error correction in case the terminal is misconfigured.  If you don’t need this, you can also use the `print()` function but it might or might now work depending on the Python version that you have.

## Linking commands
Commands can linked to one another using the `group()`. Here's an example that implements two commands for managing databases:

```Python
@quo.group()
def bind():
    pass

@quo.command()
def initdb():
    quo.echo('The database has been Initialized')

@quo.command()
def dropdb():
    quo.echo('The database has been removed')

bind.add_command(initdb)
bind.add_command(dropdb)
```
As you can see, `the group()` transform works the same way pretty much like the `command()` transform, the difference is, the `group()` function creates a Group object instead which can be given multiple subcommands that can be attached with `group.add_command()`.
It is also very much possible to automatically attach and create a command by using the `group.command()` instead of the former. The script above can be transformed by rewritting it like so:

```Python
@quo.group()
def bind():
    pass

@bind.command()
def initdb():
    quo.echo('The database has been initialized')

@bind.command()
def dropdb():
    quo.echo('The database has been removed')

if __name__ == '__main__':
    bind()
```
