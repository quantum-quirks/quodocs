---
title: Getting started
date: 2021-01-15 07:42:34
slug: getting-started
---

## What is Quo

Quo is a Python based toolkit for creating Command-Line Interface (CLI) applications. Quo improves programmer's productivity because it's easy to use and supports auto completion which means less time will be spent debugging.

## Requirements

Quo requires **Python 3+**

## Installation

<div class="termy">

```console
Install
$ pip install quo

or install and update
$ pip install -U quo
🔸🔸🔸🔸🔸💯 
Quo has been installed successfully🎉 
```

</div>

## Example

### Example 1

* Create a  file `test.py` 

```Python
import quo
quo.secho(f'Hello Gerry', fg='black', bg='cyan')

```

* Run the application
```console
$ python test.py

// Usage: quo.secho() bg=Background color, fg=Foreground color
```

### Example2
* `test.py`

```Python
import quo 
    @quo.command()
    @quo.option("--count", default=1, help="The number of times the feedback is printed.")
    @quo.option("--name", prompt="What is your name", help="This prompts the user to input their name.")
    @quo.option("--profession", prompt="What is your profession", help="This prompts user to input their proffession")
    def survey(count, name, proffession):
       
        for _ in range(count):
            quo.echo(f"Thank you for your time, {name}!")

    if __name__ == '__main__':
        survey() 
// A simple survey application
```

## Donate
In order to for me to maintain this project, `please consider donating today` 
