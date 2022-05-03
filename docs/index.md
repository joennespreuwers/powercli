<<<<<<< HEAD
# PowerCLI Commands

## Table Of Contents
[Connect to vcenter server via powercli](#uconnect-to-vcenter-server-via-powercliu)

[Find new vm's](#ufind-new-vmsu)

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
=======
## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/joennespreuwers/powercli/edit/master/docs/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/joennespreuwers/powercli/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
>>>>>>> 8b1a7586654fa3cb95abc75345811558fb3ceca7
