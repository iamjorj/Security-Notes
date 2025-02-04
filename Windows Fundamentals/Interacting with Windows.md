
# GUI

- self explanatory, it's a graphical user interface 
- users can interact with a computer without knowing any console commands or any programming languages
- Sysadmins commonly use GUI based systems to administer Active Directory, configuring IIS, and interacting with databases
# RDP

- Remote Desktop Protocol
- uses port 3389 to send data back and forth between computers
- lets the user access another computer's GUI as if they were sitting there
- used by sysadmins to administer remote systems quickly 
- allows users to access work computers from home via vpn
# Windows Command Line
- [windows command reference](https://download.microsoft.com/download/5/8/9/58911986-D4AD-4695-BF63-F734CD4DF8F2/ws-commands.pdf)
- use either cmd or powershell

# CMD.exe
- command prompt to execute commands 
- certain commands have their own help menus, accessed using `<command> /?`

# Powershell
- command shell geared towards sysadmins
- interactive command prompt, as well as a powerful scripting environment
- built upon .NET framework
- we can run the majority of the same commands as we could with a cmd shell

## Cmdlets
- small single function tools built into the powershell shell
- in the form of `verb-noun`, like `Get-ChildItem` 
- tab key cycles through arguments after `-`
## Aliases
- you know what aliases are
- `Get-Alias` gets aliases 
- `New-Alias` creates an alias

## Help
- `Get-Help <cmdname> -Online` gets the online help
- `Update-Help` downloads help files locally
## Scripts and 
- We can run scripts wow
- `Import-Module .\script.ps1` imports required modules

## Execution Policy
- if we can't run scripts it's because of a security feature called the execution policy
- prevents execution of malicious scripts
- get using `Get-ExecutionPolicy`
- change using `Set-ExecutionPolicy`

| Policy       | Description                                                                                                                                                           |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AllSigned    | All scripts can run, but a trusted publisher must sign scripts/config files. A prompt is shown whenever running scripts by publishers not listed as trusted/untrusted |
| Bypass       | nothing is blocked, no popup is shown                                                                                                                                 |
| Default      | default is Restricted for windows, and RemoteSigned for servers                                                                                                       |
| RemoteSigned | Scripts are required to be signed if it's downloaded, not required for locally written scripts                                                                        |
| Restricted   | allows individual commands, but no scripts. config files (ps1xml), module script files (psm1) and powershell profiles (ps1) are blocked                               |
| Undefined    | no execution policy defined for current scope, if all scopes are undefined, defaults to restricted                                                                    |
| Unrestricted | default for non windows, cannot be changed. allows unsigned scripts to be run, warns user before running scripts from local intranet zone                             |
