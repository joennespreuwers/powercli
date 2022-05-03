# PowerCLI Commands

## Table Of Contents
[Connect to vcenter server via powercli](#connect-to-vcenter-server-via-powercli)

[Find new vm's](#find-new-vms)

---

## Connect to vcenter server via powercli
```PowerShell
Connect-VIServer -Server 10.56.112.98 -User administrator@vsphere.local -Password D3ll3MC! -savecredentials

Connect-VIServer -Server 10.10.210.13 -User administrator@vsphere.local -Password Vxr@il123 -savecredentials

Connect-VIServer -Server mgmtvc01.rdc.bru -User administrator@vsphere.local -Password D3ll3MC! -savecredentials
```

### See current connection (if there is one)
```PowerShell
$global:defaultviserver
```

---

## Find vm's

### VxRail:
```PowerShell
Get-VM  | Where {$_.Name -match 'esx_VXR'}
```
### VMWare Cloud Foundation:
```PowerShell
Get-VM  |Where {$_.Name -match 'vcf'}
```

---

## Find NetworkAdapter's

```PowerShell
Get-VM  |Where {$_.Name -match 'esx_VXR'} | Get-NetworkAdapter
```

---

## Change NetworkAdapter's

```PowerShell
Get-VM  |Where {$_.Name -match 'esx_VXR'} |Get-NetworkAdapter  |Set-NetworkAdapter -NetworkName vVxRail_Trunk`
```

---

## List VApp (slot)

```PowerShell
Get-VApp | Where {$_.Name -match 'slot'}
```

---

## Rename VApp

```PowerShell
Get-VApp | Where {$_.Name -match 'slot0'} | set-VApp -name vVxRail-cluster-0
```

---

## Allocate memory for vm

```PowerShell
Get-VApp -name vVxRail-cluster-5 | get-vm | set-vm -MemoryGB 0 -Confirm:$false
```

---

## List Snapshot's

```PowerShell
Get-VM |Where {$_.Name -match 'vxrail-cl0-n0'}| Get-Snapshot | Select VM,Name
```

---

## Revert to snapshot

```PowerShell
Set-VM -VM vxrail-cl0-n0 -Snapshot snapshot -Confirm:$false
```