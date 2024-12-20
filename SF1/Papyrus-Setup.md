This document covers setting up the files and tools for Papyrus development.

## Extract Papyrus Source
The Papyrus source scripts are distributed with the Creation Kit.
You will not find them among the base game files.

1. After having downloaded and installed the Creation Kit, find the `Starfield\Tools\ContentResources.zip` file.
2. Extract the ZIP so that `Action.psc` along with all the other scripts & folders end up at `Starfield\Data\Scripts\Source`.



## Installing Visual Studio Code
Microsoft Visual Studio Code, also known as VS Code or VSC, is an extendable text editor for code developers of almost any language.
The editor ships with JavaScript, TypeScript, CSS, and HTML language support, but additional languages and features can by added through 3rd party extensions.
VS Code is free, open source, and runs on Windows, Linux, and Mac.

1. [Download Visual Studio Code](https://code.visualstudio.com/Download)
2. Install Visual Studio Code


## Launching Visual Studio Code
When launching VS Code for Papyrus script development, make sure to always open VS Code with the `Starfield\Data\Scripts\Source` directory.
Do not be tempted to open VSC in single file mode or any other directory.
The plugin expects the source PSC to be located at the root of the opened folder.


## Installing the VS Code Papyrus extension
As stated earlier, VS Code has an *à la carte* design where you add the editor functionality you need through downloadable extensions.
These are normally distributed through an in-editor extension manager but Bethesda has bundled theirs with the Creation Kit rather than the online Microsoft extension marketplace.

To install the bundled Bethesda extension to VS Code follow these steps.

1. Launch Visual Studio Code as described in the previous section.
2. Go to `View` -> `Extensions` then find the triple-dot hamburger menu called "Views and More Actions...". Look at the top-right corner of the extensions panel.
3. From the drop-down menu select `Install from VISX`. A .visx is a *Visual Studio Extension Installer*.
4. Navigate to `Starfield\Tools\VSCodePapyrusAddon\` and select the `vscodepapyrus-1.6.2.vsix` file.



## Preparing Workspace
This section covers creating a unique namespace folder for your mod as your project's scripts to live inside.
Navigate to `Starfield\Data\Scripts\Source` and create a new folder for your project.

Give your namespace folder a unique identifier that is unlikely to collide with someone else's namespace folder.
This collision of naming is only a concern for the root namespace folder.
Any script or namespace within your root namespace folder will not collide with any other mod.
This means that every project may have a script called `Script.psc` as long as everyone keeps their scripts to their own namespaces.
A `Scripts\Source\Scrivener\Script.psc` and `Scripts\Source\Cartogriffi\Script.psc` can coexist perfectly fine without ambiguity.

For the following sections we will using `Starfield\Data\Scripts\Source\MyProject` as a sample.



## Compiling in VS Code
This section covers how to compile Papyrus source into a Papyrus executable.

This is done by calling the `Starfield\Tools\Papyrus Compiler\PapyrusCompiler.exe` program directly.
Note that this is the same program used by the Creation Kit to compile scripts.

There are three main ways to do this in VS Code.
I will explain the last method as it is editor agnostic and Iv'e been using it longer.

- We can open the VS Code *Integrated Terminal* to call the compiler with correct parameters directly on the command line.
- We can create a VS Code *Task* which is a json file with the EXE path and parameters predefined. Running the task with execute the compiler.
- We can create a PPJ and/or a BAT file where the PPJ defines the parameters and the BAT executes the compiler.

The common thread between all these methods is a means to shove project specific parameters for your scripts into the compiler.
There are many ways to do this, but this one is mine.

Navigate to the `Starfield\Data\Scripts\Source\MyProject` sample namespace and consider the following sections.



### Create a Papyrus Project file
Now we will create a new PPJ file which encapsulates all our project specific compiler parameters.
A PPJ file is a plain text file based on standard XML, or extendable markup language.

Create a new PPJ file called `MyProject.ppj` and place it on the root of your project folder.
Lets also assume that we have three Papyrus scripts in your namespace already for demonstration purposes.

Something like this and so on..
```
ScriptName MyProject:MyScript1
{The Starfield\Data\Scripts\Source\MyProject\MyScript1.psc file.}
```

Now create the file and add this content.

@ `Starfield\Data\Scripts\Source\MyProject\MyProject.ppj`
```xml
<?xml version='1.0'?>
<PapyrusProject
	xmlns="PapyrusProject.xsd"
	Flags="Starfield_Papyrus_Flags.flg"
	Output="..\..\"
	Asm="Discard"
	Optimize="false"
	Release="false"
	Final="false"
>
	<Imports>
		<Import>..\</Import>
	</Imports>
	<Scripts>
		<Script>MyProject\MyScript1</Script>
		<Script>MyProject\MyScript2</Script>
		<Script>MyProject\MyScript3</Script>
	</Scripts>
</PapyrusProject>
```

For the most part, any project could use this PPJ as-is except for the `<Scripts>` block.
In the `<Scripts>` block you will define every script that you want compiled.
This not necessarily limited to your own namespace. You may define *any* script for compilation without establishing any dependency.
I do not recommend changing any other values here.

The XML values of note are `Output` which defines where PEX files are put after compilation is successful.
This ends up being pointed to the `Starfield\Data\Scripts` directory.
This is relative path which is resolved from the *working directory* process, or a full path can be used if you really must.

The other is `<Imports>` which defines where the dependant source needed to compile your `<Scripts>` is located.
This is the `Starfield\Data\Scripts\Source` directory expressed as a relative path.
Believe it or not, `<Scripts>` need to include themselves in the listed imports.
It is not an *additional* imports, its *all* imports.
This is just an aside that would only be relevant in advanced configurations where you have source spread over many directories.

Now proceed to the next section to create a Windows Batch script.


### Create a Windows Batch script
Create a new Windows Batch script called `Build.bat` and place it on your root *namespace* folder.
Add this single line to the file which translates to English as "Call the Papyrus compiler with our Papyrus project parameters".
Or in simpler terms.. "put ppj into exe".

Some words of caution and a tip.
- Always **be extremely skeptical of Batch or PowerShell scripts** provided by strangers on the internet. Read the content before executing or ask someone who can.
- Note that double clicking a BAT file will execute it, so use caution if you intended to *edit* the file.
- To edit a bat file without executing it, either open it in VS Code or right-click the file and select "Edit".
- If Windows throws a fit about the script just chose "download anyway" and/or "run anyway". This scare prompt will only appear once.

@ `Starfield\Data\Scripts\Source\MyProject\Build.bat`
```bat
CALL "..\..\..\..\Tools\Papyrus Compiler\PapyrusCompiler" "MyProject.ppj"
PAUSE
```

Most power users will prefer to execute this `Build.bat` from the command line or VS Code integrated terminal.
If so, remove the `PAUSE` command to save yourself pressing enter twice.
```bat
CALL "..\..\..\..\Tools\Papyrus Compiler\PapyrusCompiler" "MyProject.ppj"
```


## Running the compiler
You are now done configuring your Papyrus workspace.

As noted in the previous section, we execute the `Build.bat` by double clicking it, using the command line, or VS Code integrated terminal.
I will explain a little further on how to use the VS Code integrated terminal.

1. From within VS Code right-click your root namespace folder that contains your PPJ file and select **Open in Integrated Terminal**.
2. From the terminal panel enter the command `build`.

It is also possible to tie this in with a VS Code task, or replace these files entirely with a single task.
The choice is yours!


I have included download to serve as a starter template for Papyrus workspaces, the same described in this document.
Cheers to my friends!
