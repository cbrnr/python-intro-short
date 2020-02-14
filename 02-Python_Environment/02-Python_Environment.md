2 - Python Environment
======================
Components
----------
Python consists of the Python programming language, a Python interpreter (which is a program that can interpret and run Python code), and an extensive standard library. The reference (official) Python interpreter is written in the C programming language and is therefore called [CPython](https://github.com/python/cpython).

The Python programming language includes only relatively few keywords and built-in functions. However, the [standard library](https://docs.python.org/3/library/) vastly extends the core functionality such as additional data types, input/output, regular expressions, mathematical functions, data compression, Internet data handling, multimedia services, graphical user interfaces, and so on.

Furthermore, Python can be extended with third-party packages that are not part of the official Python distribution. Installing these packages is straightforward, because they are available from a central repository called the [Python Packaging Index (PyPI)](https://pypi.org). We will discuss how to install, update, and uninstall third-party packages later in this chapter.

As for any programming language, a good text editor is also an essential component for writing Python scripts. Good text editors include support for syntax highlighting, indentation, line numbers, code inspection, and more. For this reason, I recommend that you do not use the simple editors that come with Windows (Notepad) or macOS (TextEdit). Similarly, office suites such as Microsoft Office or LibreOffice are not suitable for programming. Instead, install and use one of the following text editors (all of them are free, open source, and available on Windows, macOS, and Linux):

- [Visual Studio Code](https://code.visualstudio.com)
- [Atom](https://atom.io)
- [Spyder](https://www.spyder-ide.org)
- [PyCharm](https://www.jetbrains.com/pycharm/)

We will use Spyder in this workshop, mainly because it comes pre-installed with Anaconda. In addition to a fully featured editor, Spyder boasts many useful features such as an integrated console running the Python interpreter, a comprehensive help system, and more. However, feel free to try out alternative editors and choose the one that best suits your needs.

The following figure summarizes the basic components of a Python environment.

![Python components](python_components.png)

Anaconda
--------


---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.