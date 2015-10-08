## Where is my python modules?

When we are developing software, it doesn't matter the language, is a common practice
to split the code in small pieces, it helps the legibility and
code organization. In the C language, for example, we create header (\*.h)
files and implementation files (\*.c). In python we have module files with
the extension `.py`. To load a module we use the `import` keyword.

An important  question that arises when we are learning python is how to find
my python modules. Look this error message: **ImportError: No module named XXX**.
Has it ever happened to you? :D Here we will try to understand a little bit more
about this problem.

To start I will create a `pub` directory and add to it a module named `drink.py`.
As I'm living in England, to drink a pint is part of my culture now. \o/

```shell
$ mkdir pub
$ touch pub/drink.py
$ echo "print('give me a pint')" > pub/drink.py
```

Lets try to import the module `drink.py`.

```shell
$ python
Python 2.7.10 (default, Jul 14 2015, 19:46:27) 
[GCC 4.2.1 Compatible Apple LLVM 6.0 (clang-600.0.39)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import drink
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
ImportError: No module named drink
```
