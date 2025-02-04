
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
