# Getting ready #

HELP me
* use the Update-Help cmdlet to download and install the newest help files on your computer.
* use the Get-Help cmdlet to display help.
* use -WhatIf and -Confirm parameter
        Get-Service -DisplayName *bi* | Stop-Service -WhatIf

RUN scripts
* the default execution policy on Windows PowerShell is Restricted. This policy allows you to run cmdlets, but not scripts.
* use the Set-ExecutionPolicy cmdlet to change the execution policy to AllSigned or RemoteSigned.

Enable remoting
* run the Enable-PSRemoting cmdlet on the computer that you want to manage remotely.
* on Windows Server 2008 (not Windows Server 2008 R2), you must re-enable remoting after installing Windows Management Framework 3.0.

# Fundamentals #

## [new Features contrast to cmd(tradition shell)](https://docs.microsoft.com/en-us/powershell/scripting/getting-started/fundamental/about-windows-powershell?view=powershell-5.1) ##

### Discoverability ###

        Get-Command *-Service
        Get-Help Get-Service
        Get-Service | Get-Member

### Consistency ###

> For example, if you learn how to use the Sort-Object cmdlet, you can use that knowledge to sort the output of any cmdlet. You do not have to learn the different sorting routines of each cmdlet.

### Interactive and Scripting Environments ###

> Windows PowerShell is a combined interactive and scripting environment that gives you access to command-line tools and COM objects, and also enables you to use the power of the .NET Framework Class Library (FCL). 

> This environment improves upon the Windows Command Prompt, which provides an interactive environment with multiple command-line tools. It also improves upon Windows Script Host (WSH) scripts, which let you use multiple command-line tools and COM automation objects, but do not provide an interactive environment.

无论是在命令行提示符（Command Prompt），还是在windows脚本宿主（Windows Script Host）中运行，都可以与command-line tools、 COM（component object model）以及.net framewor class library 交互（Windows Script Host中运行时，不提供交互式环境）。

Windows Script Host overview
> You can use Windows Script Host to run scripts by clicking a script file on the Windows desktop or by typing the name of a script file at the command prompt. Similar to Microsoft Internet Explorer, Windows Script Host serves as a controller of Windows Script-compliant scripting engines. Unlike Internet Explorer, Windows Script Host has very low memory requirements and is ideal for both interactive and non-interactive scripting, such as logon scripting and administrative scripting. 

### Object Orientation ###

> It extends the concept of sending data between commands by enabling you to send objects, rather than text.

### Easy Transition to Scripting ###

> You can type commands at the Windows PowerShell command prompt to discover the commands that perform a task.
> Then, you can save those commands in a transcript or a history before copying them to a file for use as a script.

***

## [Exploring the Windows PowerShell ISE](https://docs.microsoft.com/en-us/powershell/scripting/getting-started/fundamental/exploring-the-windows-powershell-ise?view=powershell-5.1) ##

***

## [Getting Detailed Help Information](https://docs.microsoft.com/en-us/powershell/scripting/getting-started/fundamental/getting-detailed-help-information?view=powershell-5.1) ##

Getting Help for Cmdlets

        get-help get-childitem
or
        get-childitem -?

        get-help -category cmdlet           #get a list of all the cmdlet Help topics in your session
        get-help get-childitem -detailed    #use the Detailed parameter
        get-help get-childitem -parameter * #get detailed Help about the parameters of a cmdlet
        get-help get-childitem -examples    #display only the examples in a Help topic

Getting Conceptual Help

> Conceptual Help topics begin with the "about_" prefix, such as about_line_editing.

        get-help about_*
        get-help about_command_syntax

Getting Help About Providers

        get-help registry
        get-help -category provider

Getting Help About Scripts and Functions

        get-help mkdir

Getting Help Online

        get-help <command-name> -online

> If you are connected to the Internet, one of the best ways to get Help is to view the Help topics online. Because online topics are easy to update, they are likely to provide the most current content.

***

## [Getting Information About Commands](https://docs.microsoft.com/en-us/powershell/scripting/getting-started/fundamental/getting-information-about-commands?view=powershell-5.1) ##

        Get-Command Get-Help -Syntax

> The Get-Command command does not list every command that is available in Windows PowerShell.
> Windows PowerShell actually supports several other types of commands. Aliases, functions, and scripts are also Windows PowerShell commands.
> External files that are executable, or have a registered file type handler, are also classified as commands.
To get all of them:

        Get-Command *

To get command aliases, which are the assigned nicknames of commands, type:
        Get-Command -CommandType Alias
        
To get the functions in the current session, type:        
        Get-Command -CommandType Function

To display scripts in Windows PowerShell's search path, type:
        Get-Command -CommandType Script

***

## [Learning Windows PowerShell Names](https://docs.microsoft.com/en-us/powershell/scripting/getting-started/fundamental/learning-windows-powershell-names?view=powershell-5.1) ##

### Cmdlets Use Verb-Noun Names to Reduce Command Memorization ###

### Cmdlets Use Standard Parameters ###

**The Help Parameter**
> Parameter names always have a '-' prepended to them when you use them.
> When you specify the -? parameter to any cmdlet, the cmdlet is not executed. Instead, Windows PowerShell displays help for the cmdlet.

**Common Parameters**
> Windows PowerShell has several parameters known as **common parameters**. 
> The **common parameters** are WhatIf, Confirm, Verbose, Debug, Warn, ErrorAction, ErrorVariable, OutVariable, and OutBuffer.

**Suggested Parameters**
> Among the important suggested parameter names are Force, Exclude, Include, PassThru, Path, and CaseSensitive.

***

## [Understanding Important Windows PowerShell Concepts](https://docs.microsoft.com/en-us/powershell/scripting/getting-started/fundamental/understanding-important-windows-powershell-concepts?view=powershell-5.1) ##

### Commands Are Not Text-Based ###

### The Command Family Is Extensible ###

### Windows PowerShell Handles Console Input and Display ###
> When you enter a command in Windows PowerShell, everything you enter is automatically parsed and pre-processed by Windows PowerShell. 
> If you use the -? parameter with a Windows PowerShell cmdlet, it always means "show me Help for this command". 
> Cmdlet developers **do not** have to parse the command; they only need to provide the Help text.

###  Windows PowerShell Uses Some C# Syntax ###

***

## [Object Pipeline](https://docs.microsoft.com/en-us/powershell/scripting/getting-started/fundamental/understanding-the-windows-powershell-pipeline?view=powershell-5.1) ##

> Instead of using text to let commands in a pipeline communicate, Windows PowerShell uses objects. From the standpoint of a user, objects package related information into a form that makes it easier to manipulate the information as a unit, and extract specific items that you need.

## [Alias](https://docs.microsoft.com/en-us/powershell/scripting/getting-started/fundamental/using-familiar-command-names?view=powershell-5.1) ##

        Get-Alias cls

### Interpreting Standard Aliases ###

> Windows PowerShell tries to compromise between clarity and brevity by providing a set of standard aliases that are based on shorthand names for common verbs and nouns. 
> the verb **Get** is abbreviated to **g**, the verb **Set** is abbreviated to **s**, the noun **Item** is abbreviated to **i**, the noun **Location** is abbreviated to **l**, and the noun **Command** is abbreviated to **cm**. 

### Creating New Aliases ###

        Set-Alias -Name gi -Value Get-Item
        Set-Alias -Name si -Value Set-Item
        Set-Alias -Name gl -Value Get-Location
        Set-Alias -Name sl -Value Set-Location
        Set-Alias -Name gcm -Value Get-Command

## [Using Variables to Store Objects](https://docs.microsoft.com/en-us/powershell/scripting/getting-started/fundamental/using-variables-to-store-objects?view=powershell-5.1) ##

> Variables are always specified with the initial character $, and can include any alphanumeric characters or the underscore in their names. 

### Creating a Variable ###

        $loc
        $loc = Get-Location
        $loc | Get-Member -MemberType Property

### Manipulating Variables ###

You can see a complete listing in a readable form by typing:

        Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap

Type the following command to clear all variables:

        Remove-Variable -Name * -Force -ErrorAction SilentlyContinue

display all PowerShell variables by typing:
        Get-Variable
        Get-ChildItem variable:

### Using Cmd.exe Variables ###

It can use the same variables available in any environment in Windows,These variables are exposed through a drive named env:

        Get-PSDrive         # Gets drives in the current session.
        Get-ChildItem env:

Although the standard variable cmdlets are not designed to work with env: variables, you can still use them by specifying the env: prefix. For example, to see the operating system root directory, you can use the command-shell %SystemRoot% variable from within PowerShell by typing:

        $env:SystemRoot

***

