# Getting ready #

HELP me
* use the Update-Help cmdlet to download and install the newest help files on your computer.
* use the Get-Help cmdlet to display help.

RUN scripts
* the default execution policy on Windows PowerShell is Restricted. This policy allows you to run cmdlets, but not scripts.
* use the Set-ExecutionPolicy cmdlet to change the execution policy to AllSigned or RemoteSigned.

Enable remoting
* run the Enable-PSRemoting cmdlet on the computer that you want to manage remotely.
* on Windows Server 2008 (not Windows Server 2008 R2), you must re-enable remoting after installing Windows Management Framework 3.0.

# Fundamentals #

## new Features contrast to cmd(tradition shell) ##

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

## Getting Detailed Help Information ##

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

## Getting Information About Commands ##