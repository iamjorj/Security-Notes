# What is Windows Server Core

- minimalistic server environment containing only key funtionality
- lower management requirements, smaller attack surface, uses less disk space
- all config/maintenance tasks are performed using command line, or remote management using MMC or RSAT
- some GUI programs are supported (such as Registry Editor, Notepad, System Information, Windows Installer, Task Manager, and PowerShell)
- cannot convert to desktop experience
- some applications cannot run on this
- tldr less resource intensive, harder to manage and has steeper learning curve
## Functions

has
- cmd
- powershell/.net
- regedit
- taskmgr
- remote desktop services 

does not have
- diskmgmt.msc
- server manager
- mmc
- eventvwr
- services.msc
- control panel
- windows explorer
- internet browser