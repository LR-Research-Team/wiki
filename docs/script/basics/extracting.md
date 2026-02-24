In this section, you will learn how to generate your codebase from the game files and setup the necessary tools for editing the scripts.

* Download the [WhiteCLBtool archive](https://mega.nz/file/2p4BQKxa#KqBYLBL2t2-cEPuz7UH-jlwPdKciZ9eq_ZaqHIFuIxE) and unzip it. by doing so, you will get a folder, inside which the WhiteCLBtool program will be present along with a Libraries folder.

* We will need to install Java SDK version 19 or above, for decompilng the CLB files with the WhiteCLBtool. go to the [Oracle website and download the Java SDK](https://www.oracle.com/in/java/technologies/downloads/) and install it.


## Setting up your code editor

We will require an code editor program to view or write our clb scripts. for this, we can go either with IntelliJ IDEA or VS Code and so depending on your choice, use one of the setup links given below:

* [Setting up IntelliJ](./setup-intellij.md)

* [Setting up VS Code](./setup-vscode.md)

## Generating your codebase

!!! note

    This section assumes that you have already setup the code editor and have unpacked your game files with the Nova Chrysalia mod manager.



* Copy the path of your game folder, for which you want to generate the codebase. example of Final Fantasy XIII's  game folder path on my PC, is given below:
``` 
"S:\Steam Library Games 2\steamapps\common\FINAL FANTASY XIII"
```

* Now open a terminal or command prompt inside the folder where you the WhiteCLBtool program is present and in the terminal, type `WhiteCLBtool -d` along with the path to your game's folder. example with Final Fantasy XIII's game folder path on my PC, is once again given below:
```
WhiteCLBtool -d "S:\Steam Library Games 2\steamapps\common\FINAL FANTASY XIII"
```

* The tool will start converting all the clb files of the game to clean .java files with proper folder structure and then will move the .java files, inside a **clbs_decompiled** folder. this particular folder will be generated inside the game folder and you can move this folder elsewhere and rename it to something more meaningful like **"FFXIIICodebase"** for example.

That's it, the codebase is now ready to be used for reading and writing clb scripts.

* This is an optional step and I recommend doing it only if you are interested in doing so. <br>You can use WhiteCLBtool to arrange the decompiled java files, into nicely organized directories which can help in getting a proper codebase folder structure used during development before building the game project from the engine. this can be done by running the tool with the `-a` switch along with the clbs_decompiled folder as the argument.<br>example with Final Fantasy XIII's game folder path on my PC, is once again given below:
```
WhiteCLBtool -a "S:\Steam Library Games 2\steamapps\common\FINAL FANTASY XIII\clbs_decompiled"
```
Once the function has finished executing, all the java files should be copied into a **clbs_arranged** folder in correct directories. do keep in mind that the zone java files requires the cmn, fake, and fld folders to be placed inside each z#### folder. the mentioned folders contain important java related scripts, which the zone scripts can access and the reason this tool doesn't do this automatically with the arrange function, is due to the issue of duplication. so this is left to you the user, to manually do it for whatever zone's scripts you are interested in looking at.

You can now proceed to this [page](./repacking.md) to setup the repacking utilities.