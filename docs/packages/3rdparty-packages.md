---
description: '3rd Party NuGet Packages on https://packages.gkdatacenter.net/'
---

# 3rd Party NuGet Packages

## PowerShell Modules

### PSIni

* Used to read and write ini files from within Chocolatey or craft packages
* Source & License: [https://www.powershellgallery.com/packages/PsIni](https://www.powershellgallery.com/packages/PsIni)
* Project Home: [http://lipkau.github.io/PsIni/](http://lipkau.github.io/PsIni/)

Use: Deploy as package through RealmJoin \(or add dependency in nuspec, e.g.: `<dependency id="PSini" version="[2.0,3.0)" />`\)  
 Import: `Import-Module "$env:ProgramData\chocolatey\lib\PSini\PsIni.psm1"`

