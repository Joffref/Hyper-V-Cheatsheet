# Commands

## General
List all the commands in a grid style :
```powershell
Get-Command -Module hyper-v | Out-GridView
```

Show the help menu of a command : 
```powershell
Get-Help <Command>
```

## VM
List all your VM
```powershell
Get-VM
```
Output :

[![Output of Get-VM command](https://docs.microsoft.com/fr-fr/virtualization/hyper-v-on-windows/quick-start/media/get_vm.png)](https://docs.microsoft.com/fr-fr/virtualization/hyper-v-on-windows/quick-start/try-hyper-v-powershell#return-a-list-of-virtual-machines)]

Constraint list of your VM using [Where](https://docs.microsoft.com/fr-fr/previous-versions/windows/it-pro/windows-powershell-1.0/ee177028(v=technet.10))
```powershell
 Get-VM | where {condition} 
```
Exemple :
List all the VM powered on :
```powershell
 Get-VM | where { $_.State -eq 'Running' } 
```
