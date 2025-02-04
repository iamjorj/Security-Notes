## What is WMI

- Powershell tool for system monitoring
- Consolidates device and application management across corporate networks
- comes preinstalled with windows
## Common uses

- get status information for local/remote systems 
- configuring security settings on remote machines
- setting/changing user and group permissions
- running code
- scheduling processes
- setting up logging

## How to use

### CMD
`WMIC` opens interactive shell
can run commands directly such as `wmic computersystem get name`
list commands and aliases with `wmic /?`

### Powershell
uses the Get-WmiObject module
can use the Invoke-WmiMethod module to call the methods of wmi modules


## Components

| Component Name     | Description                                                                                                              |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| WMI Service        | WMI process, runs automatically at boot, acts as intermediary between WMI providers, WMI repo, and managing applications |
| Managed Objects    | Logical/Physical components managed by WMI                                                                               |
| WMI providers      | Objects that monitor events/data related to a specific object                                                            |
| Classes            | Used by WMI proivider to pass data to WMI service                                                                        |
| Methods            | Attached to classes and allows actions to be performed e.g. starting/stopping process on remote machines                 |
| WMI repo           | database that stores static data related to WMI                                                                          |
| CIM Object Manager | System that requests data from WMI providers and returns it to application that requested it                             |
| WMI api            | enables applications to access the wmi infrastructure                                                                    |
| WMI consumer       | Sends queries to objects using the CIM Object manager                                                                    |
