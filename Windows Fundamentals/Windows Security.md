
- windows is easily misconfigured, allowing for many attack vectors
- many abusable features, many critical vulnerabilities
- microsoft has been adding new features to harden systems

# Security Identifier (SID)

- each security principal is given a unique sid
	-  security principal is user, group, or computer account
- stored in security database
- added to users access token to identify which actions user is allowed to take
- consists of Identifier Authority, and the Relative ID (RID)
- in an AD (active directory) environment, SID also includes domain SID

 Format:
S-1-5-21-674899381-4069889467-2080702030-1002
`(SID)-(revision level)-(identifier-authority)-(subauthority1)-(subauthority2)-(etc)`


| Number                          | Meaning              | Description                                                                                                                                                                                        |
| ------------------------------- | -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| S                               | SID                  | Identifies string is SID                                                                                                                                                                           |
| 1                               | Revision Level       | amount of changes (currently unchanged, at 1)                                                                                                                                                      |
| 5                               | Identifier-Authority | A 48-bit string that identifies the authority (the computer or network) that created the SID.                                                                                                      |
| 21                              | Subauthority1        | This is a variable number that identifies the user's relation or group described by the SID to the authority that created it. It tells us in what order this authority created the user's account. |
| 674899381-4069889467-2080702030 | Subauthority2        | Tells us which computer (or domain) created the number                                                                                                                                             |
| 1002                            | Subauthority3        | The RID that distinguishes one account from another. Tells us whether this user is a normal user, a guest, an administrator, or part of some other group                                           |
# Security Accounts Manager (SAM) and Access Control Entries (ACE)

- SAM grants rights for a network to run specific processes
- the access rights are managed by Access Control Entries (ACEs) in Access Control Lists (ACLs)
- ACLs contain ACEs that define which users, groups, or processes have access to execute a process
- Permissions to access a securable object is given by a security descriptor, classified into 2 types of ACLs: Discretionary Access Control List (DACL) or System Access Control List (SACL).
- Every thread and process started or initiated by a user goes through an authorization proces
- access tokens are validated by the Local Security Authority (LSA)
- access tokens contain SIDs as well as other security-relevant information
- this is important for privesc

# User Account Control (UAC)
- prevents malware from running or manipulating processes that can damage a computer
- Admin Approval Mode (prompt when needing admin permissions, e.g installing software)
- the prompt halts the execution of scripts/binaries that attempt execution, until the user/admin enters the password
![uac](https://academy.hackthebox.com/storage/modules/49/uacarchitecture1.png)

# Registry
- hierarchical database of low level settings
- very important to the windows OS
- divided into computer specific data, and user specific data 
- open the registry editor using the `regedit` command
- File structure consists of main folders (rootkeys) and subfolders (subkeys)
- Each folder under `Computer` is a key
- root keys start with `HKEY`
- system registry is stored under `C:\Windows\System32\Config`
- current user registry is stored under `C:\Users\<username>\Ntuser.dat`
## Subkey Types

| value                   | type                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| REG_BINARY              | Binary data in any form.                                                                                                                                                                                                                                                                                                                                                                                              |
| REG_DWORD               | A 32-bit number.                                                                                                                                                                                                                                                                                                                                                                                                      |
| REG_DWORD_LITTLE_ENDIAN | A 32-bit number in little-endian format. Windows is designed to run on little-endian computer architectures. Therefore, this value is defined as REG_DWORD in the Windows header files.                                                                                                                                                                                                                               |
| REG_DWORD_BIG_ENDIAN    | A 32-bit number in big-endian format. Some UNIX systems support big-endian architectures.                                                                                                                                                                                                                                                                                                                             |
| REG_EXPAND_SZ           | A null-terminated string that contains unexpanded references to environment variables (for example, "%PATH%"). It will be a Unicode or ANSI string depending on whether you use the Unicode or ANSI functions. To expand the environment variable references, use the [**ExpandEnvironmentStrings**](https://docs.microsoft.com/en-us/windows/win32/api/processenv/nf-processenv-expandenvironmentstringsa) function. |
| REG_LINK                | A null-terminated Unicode string containing the target path of a symbolic link created by calling the [**RegCreateKeyEx**](https://docs.microsoft.com/en-us/windows/desktop/api/Winreg/nf-winreg-regcreatekeyexa) function with REG_OPTION_CREATE_LINK.                                                                                                                                                               |
| REG_MULTI_SZ            | A sequence of null-terminated strings, terminated by an empty string (\0). The following is an example: _String1_\0_String2_\0_String3_\0_LastString_\0\0 The first \0 terminates the first string, the second to the last \0 terminates the last string, and the final \0 terminates the sequence. Note that the final terminator must be factored into the length of the string.                                    |
| REG_NONE                | No defined value type.                                                                                                                                                                                                                                                                                                                                                                                                |
| REG_QWORD               | A 64-bit number.                                                                                                                                                                                                                                                                                                                                                                                                      |
| REG_QWORD_LITTLE_ENDIAN | A 64-bit number in little-endian format. Windows is designed to run on little-endian computer architectures. Therefore, this value is defined as REG_QWORD in the Windows header files.                                                                                                                                                                                                                               |
| REG_SZ                  | A null-terminated string. This will be either a Unicode or an ANSI string, depending on whether you use the Unicode or ANSI functions.                                                                                                                                                                                                                                                                                |
Source: https://docs.microsoft.com/en-us/windows/win32/sysinfo/registry-value-types

### Run and RunOnce Registry Keys

- Registry hive: contains a group of keys, subkeys, and values to support files and software being loaded into memory when the OS is started, or the user logs in

`
```
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnce
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunOnce
```
editing these keys will let you run programs on startup for either the current user, or all users (local machine)

example:

```
PS C:\htb> reg query HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run

HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
    OneDrive    REG_SZ    "C:\Users\bob\AppData\Local\Microsoft\OneDrive\OneDrive.exe" /background
    OPENVPN-GUI    REG_SZ    C:\Program Files\OpenVPN\bin\openvpn-gui.exe
    Docker Desktop    REG_SZ    C:\Program Files\Docker\Docker\Docker Desktop.exe
```

# Application Whitelisting

Whitelist: a list of approved software allowed to be present and run on a system

- protects environment from malware and unapproved software
- should be implemented in audit mode to make sure software is not accidentally blocked by an error

Blacklist: a list of disallowed software

- causes the sysadmin to constantly update
- much easier to maintain a whitelist

Whitelisting is generally recommended especially in high security environments

## Applocker

- Microsoft's application whitelisting software
- gives granular control over executables, scripts, windows installer files, dlls, packaged apps, and packed app installers
- lets you create rules based on publisher name, product name, file name, version, filepath, and hashes
- can either apply rules to security groups, or individual users
- use audit mode at first

# Local Group Policy

- allows sysadmins to configure policy settings
- gpedit.msc

# Windows Defender

- Windows' built in antivirus
- managed within security center in settings
- it's not actually that bad in terms of bloat, scans folders and doesn't add trackers/browser extensions
- `Get-MpComputerStatus` gets the enabled security features
- will pick up payloads from pentesting tools
- still possible to bypass windows defender although it's becoming much more difficult