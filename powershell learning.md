# Getting ready #

about HELP
* use the Update-Help cmdlet to download and install the newest help files on your computer.
* use the Get-Help cmdlet to display help.

how to run scripts
* the default execution policy on Windows PowerShell is Restricted. This policy allows you to run cmdlets, but not scripts.
* use the Set-ExecutionPolicy cmdlet to change the execution policy to AllSigned or RemoteSigned.

Enable remoting
* run the Enable-PSRemoting cmdlet on the computer that you want to manage remotely.
* on Windows Server 2008 (not Windows Server 2008 R2), you must re-enable remoting after installing Windows Management Framework 3.0.

# Fundamentals #

## new Features contrast to cmd(tradition shell) ##

Discoverability

        Get-Command *-Service
        Get-Help Get-Service
        Get-Service | Get-Member