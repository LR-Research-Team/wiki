# Contributing

## Prerequisites
* Python
* VS Code (you can use another IDE if you want)

## Setting up your local repository
* Fork this repository and clone the fork on your computer
* Go to the resulting "wiki" folder, launch a command prompt then create a python virtual environment with ```python -m venv venv```
* Activate it with ```.\venv\Scripts\activate.bat```
* Install mkdocs material by typing ```python -m pip install mkdocs-material```
* That's it, open your repository in vscode using ```code .```

## Previewing your local version of the wiki

* In VSCode, go to Terminal -> New Terminal
* Type ```.\venv\Scripts\mkdocs.exe serve``` to build and run your local copy
* You will then be able to see it at [http://127.0.0.1:8000/](http://127.0.0.1:8000/).

The local copy will automatically update when you save your pages. You can also stop it from running by typing CTRL-C in the terminal.

## Writer guide

The only things you will have to edit will be:

* The **docs** folder, where you will put your new pages and graphics assets
* The very bottom of the **mkdocs.yml** file to change the wiki's layout, in the **nav** section.

Check out the existing pages for reference about how to use certain features, the [mkdocs material reference page](https://squidfunk.github.io/mkdocs-material/reference/) is also a great resource.

## Sharing your new content

Once your new page(s) have been created, simply make a pull request or send us your new files directly.
