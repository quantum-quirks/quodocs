---
title: Basic Concepts
date: 2018-09-15 07:42:34
slug: theme-configuration
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

