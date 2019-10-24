# GlobalEmbedObject-Template
A Clarion Global Embed Object Class Template 

The purpose of this template is to have globally as many as like to, class instances shown in the Global Embed Area 
of the IDE. This, the same way the Global Objects Error Manager (ErroClass) File Managers, Fuzzy Matcher (FuzzyClass),
INI Manager (INIClass) and Relation Managers are presented. Meaning having a tree presentation of the class instance
embed area. Moreover, also being able to create derived procedures within the class instances.

To repeat my self, this Clarion template will make it possible to add, as many as we like to, instances of a Clarion
object class in the IDE within the Global Area. At the same time, we may create derive procedures within the instance 
itself. 

For example, we want an instance of the AsciiFileClass from Clarion, by inserting the GlobalEmbedObject
extension template will permit to do so. By providing the following within the extension template window it will make
it possible:

Object Name: AscIIFileObject
Base Class:  AsciiFileClass

If the need to create a Derive class is required 
By checking the Derive check box will permit as many as we like procedures within the AscIIFileObject class instance
as well its Class Properties.

When we add these class instances, there is one thing important to know and understand. If we are compiling the program
without doing anything else the compiler will post an unresolved or exception error. The cause of this, the compiler
needs to know what to do, is it gone be in an exe or a dll. Therefore, we need to set the compiler  LINK and DLL
symbols' directives in the Project Options Compiler Tab manually. This setting is shown in the Project sub menu.
For many Clarion ABC classes the LINK compiler symbols directives is _ABCLinkMode_ and for the DLL is _ABCDllMode_. 
If the program is an EXE, we need to assign _ABCLinkMode_=1 and _ABCDllMode_=0 otherwise, a DLL will be assigned in reverse
as _ABCLinkMode_=0 and _ABCDllMode_=1.

For the above reason the Project Compiler Symbol Settings area of the extension GlobalEmbedObject template is added.
By checking "Enabling Project Compiler Symbol Settings" the Defined Symbols area will appear. This  is where we need
to add the LINK and DLL symbols of the class. Both the LINK and the DLL symbols needed to be set under;
"Enabling compiler options" the radio button Link Mode or Dll Mode.

In our example
Defined Symbols
Link project compiler defined symbol : _ABCLinkMode_
Dll project compiler defined symbol:    _ABCDllMode_

Enabling compiler options
"Radio button" Link Mode
"Radio button" Dll Mode 

By selecting "Radio button" Link Mode will assign _ABCLinkMode_ = 1 and _ABCDllMode_=0 otherwise if
"Radio button" Dll Mode is selected _ABCLinkMode_=0 and _ABCDllMode_=0


This aspect for which it is important to take care of, is the project compiler symbol directives must be set otherwise errors will appear.



However, it is important to read the tab notes regarding his usage. Actually, this may be applied to other areas that make changes to the Global Embed Area. One, if, for some reason, you need to delete an extension or a derive procedure or renaming the class instance, the need to save the app exit from the application solution and return to the session will prevent the IDE to crash. The reason for doing like so, if we are getting back right after doing the above changes to the Global Embed aread, the Clarion IDE will crash, like I said by saving the app session and reloading it, the change will be made and shown correctly.


Like said this template is taking care of the Project Compilier Symbol Settings. The only thing we need to know is 
what are the LINK and DLL symbols the parent class is using. The locations of these symbols are in the include files
where the classes are declared. The folders where they are placed usually are in the Clarion\LibSrc\win and 
Clarion\Accessory\LibSrc\Win. Here in the below example, the file is located in the Clarion\LibSrc\win folder
under ABASCII.INC file with the below header declaration. The symbol is an attribute of the class declaration
here; the LINK attribute is _ABCLinkMode_ and the DLL attribute is _ABCDllMode_.


Here's where we see these attributes in the ABASCII.INC file
AsciiFileClass      CLASS,TYPE,MODULE('ABASCII.CLW'),LINK('ABASCII.CLW',_ABCLinkMode_),DLL(_ABCDllMode_)

Below are the four tabs the first one is the setting and the others are explanatory

_____________________________________________________________________________________________________________________________
Class TAB
_____________________________________________________________________________________________________________________________

The first box is the Class Definition

Object Name:  <NameOfTheClassInstance> AsciiFileObject

Usually "Use Application Builder Class" is always check,  this will make it possible to create an instance of a class. This way we may select our Base Class from the drop down menu

in our case

Base Class: AsciiFileClass

If we need Derive procedure by checking the Derive box will enable the creation of derive procedure and its properties.

The next box area of the Class TAB is the Project Compiler Settings

If the Projects Compiler Symbol Settings is enabled the values to the symbols will be added or modified to the Project
Compiler Options

Checking box Enabling Project Compiler Settings

The following will be explained letter within the text.

If  Export Project Compiler Symbol is Enabled only the Export project symbol is required 
otherwise a LinkMode and DllMode project symbols are required

By checking box "Enabling Export Project Symbol Setting" will make the alternative way to declare symbols directives.

The Export define symbols box appears we must provide a unique symbol and optionnally checking the box "Enabling export project if check"

_____________________________________________________________________________________________________________________________
Extension Important Note
_____________________________________________________________________________________________________________________________

 When changing or deleting base class

 1) Regarding the Base Class, if, for some reason, we need to change or delete the ABC class from the GlobalEmbedObject extension, it may be    
       done here. Before getting to the Global Embeds we must save the app, exit from the app solution and reload the application otherwise, the  
        application in the IDE will crash.

 2) If other settings are changed, like renaming the class name or alteration to the project compiler settings, there is no need to exit from the 
      application. We do not have to worry about getting back to the Global Embed. We may go directly to the area.

Understanding Project Compiler Symbol Settings

 1) Regarding Project Symbol Settings, if the same defined symbols are used in multiple GlobalEmbedObject extensions the settings must be 
      identical in each extension instance otherwise error may occur.
      As an example if _ABCLinkMode_=1 and _ABCDIIMode_=0, therefore, all extension settings must be duplicated or the other extension Project     
      Symbol Settings are unchecked meaning the assignment to the project definition is disabled. Like so, we are preventing the error occurring and 
      the application will compile and run correctly.

 2) Base on what said about the point 1 above, only one project defined is sent to the project compiler defined symbols.

 3) The good thing having this assigns here we know which symbol definition represents the class of the embedded object and its status.

 4)  If, for some reason, the compiler symbols are missing in the Project Compiler Options, and here the Project Compiler Symbol Settings is 
       disabled; the application will not run the exception or an unresolve error will appear, unless some other area through the application is taking 
       care of the defined compiler symbols.

_____________________________________________________________________________________________________________________________
Project Symbol Settings Explained
_____________________________________________________________________________________________________________________________

 The compilation project symbol is required by the compiler.

The settings below will add the values under the Project Options Compiler Tab within the conditionals compilation symbols list.
A project symbol for a LINK set at 0 or 1 
A project symbol for a DLL, set at 0 or 1

Example:
The ABC class the project symbols are when it is linked to an exe file, 
for a DLL is_ABCDIIMode_ = 0 
for a EXE is ABCLinkMode =1

NOTE

 1) If the project symbol settings are not done here, it will need to be added within the Project Options Compiler Tab manually.

 2) Regarding the project symbol settings, if the same project symbol is reused in a multiple class object only one class object may 
      enable the project symbol settings. The others may be disabled if not only a single class object that uses the project symbol 
      settings will be added to the compiler conditional project options.

 3) If enabled on multiple GlobalEmbedObject extensions, the settings to subsequent class object will be then only informative.

 4) When multiple class objects use the same project symbols settings if the choice is over Export Project Symbol, then subsequent 
      GlobalEmbedObject extension must also enable the Export Project Symbol Setting with the identical value otherwise the 
      compiler will generate duplicate messages over the project symbols.

 5) Regarding identical Export Project Symbol on multiple GlobalEmbedObject extension templates, the assignment must have the 
      same state value otherwise an unresolved error will appear; the program will not compile successfully.

_____________________________________________________________________________________________________________________________
Export File Explained
_____________________________________________________________________________________________________________________________

 

The purpose having only one project symbols. When the export project symbol setting is set to 1 then the compiler will link to an exe otherwise to 0 it will compile as a Dll. This without the need, to create two defined compile symbols.

Example on an Export file on how its made

A file with the following equates that will represent the LinkMode and DIIMode of a class object Name of this file is jcClassProjectOptions.inc

Code in jcClassProjectOptions.inc 

ABCIncludeFile(Joliciel)
  OMIT(xTERMINATORx,_Export_Joliciel_Classes_) 
_JCLinkMode_  EQUATE(0)
_JCDIIMode_    EQUATE(1) 
xTERMINATORx

COMPILE(xTERMINATORx,_Export_Joliciel_Classes_)
_JCLinkMode_ EQUATE(1)
_JCDIIMode_   EQUATE(0) 
xTERMINATORx


If the Export project symbol Setting is enabled, there is no need to assign and add values to the link and dll modes of a class object only the export project symbol. In the case above if JcClassProjectOptions_ = 1 the OMIT and COMPILE statements are executed otherwise the OMIT and COMPILE are not executed

The following INCLUDE statement is inserted at the top of the declaration file < FileNameOfClass.inc>

Code in FileNameOfClass.inc

ABCIncludeFile(Joliciel)
               INCLUDE('jcClassProjectOptions.inc’),ONCE

