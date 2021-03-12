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
>Output :

>[![Output of Get-VM command](https://docs.microsoft.com/fr-fr/virtualization/hyper-v-on-windows/quick-start/media/get_vm.png)](https://docs.microsoft.com/fr-fr/virtualization/hyper-v-on-windows/quick-start/try-hyper-v-powershell#return-a-list-of-virtual-machines)]

Constraint list of your VM using [Where](https://docs.microsoft.com/fr-fr/previous-versions/windows/it-pro/windows-powershell-1.0/ee177028(v=technet.10))
```powershell
 Get-VM | where {condition} 
```
>Exemple :
>List all the VM powered on :
>```powershell
> Get-VM | where { $_.State -eq 'Running' } 
>```

Start a VM :
```powershell
Start-VM -Name <virtual machine name>
```

>It is possible to concatenate those commands
>
>For exemple, start all the VMs powered off :
>>```powershell
>>Get-VM | where {$_.State -eq 'Off'} | Start-VM
>> ```

Snapshot a VM :
```powershell
Get-VM -Name <VM Name> | Checkpoint-VM -SnapshotName <name for snapshot>
```

### Scripting
Use Windows PowerShell (ISE).

Script a deployement of a VM :
```powershell
$VMName = "VMNAME" #Name of your VM

 $VM = @{ #Initialize all the options of the VM
     Name = $VMName 
     MemoryStartupBytes = 2147483648 #RAM size, it is possible to use : GB, MB, KB
     Generation = 2 #Specifies the generation : 1 or 2
     NewVHDPath = "C:\Virtual Machines\$VMName\$VMName.vhdx" #Path of VHD
     NewVHDSizeBytes = 53687091200 #Size of VHD
     BootDevice = "VHD" 
     Path = "C:\Virtual Machines\$VMName" #Path of config storage
     SwitchName = (Get-VMSwitch).Name #Network switch where your VM will be connected on
 }

 New-VM @VM #Create a new VM using the $VM you initialized 
```
For mor info on : [New-VM](https://docs.microsoft.com/fr-fr/powershell/module/hyper-v/new-vm?view=win10-ps)
