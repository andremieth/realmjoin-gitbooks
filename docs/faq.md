# FAQ

## Which links should I bookmark?

* RealmJoin Admin Portal:  

    [https://realmjoin-web.azurewebsites.net/](https://realmjoin-web.azurewebsites.net/)

* Gitlab Packages:  

    [https://gitlab.glueckkanja.net/](https://gitlab.glueckkanja.net/)

* General RealmJoin website:  

    [https://realmjoin.com/](https://realmjoin.com/)

* Documentation:  

    [https://glueckkanja.gitbook.io/realmjoin/](https://glueckkanja.gitbook.io/realmjoin/)

## Am I able to maintain my own packages and updates?

RealmJoin contains an internal application store compatible with Intunewin, with over 500 existing applications. Glück&Kanja Consulting offers packaging-as-a-service to provide any missing applications. Also, it is possible to use additional deployment repositories completely maintained independently.

## Which platforms are supported?

RealmJoin v4 is only available for Windows 10.

## I do not see my groups in the Admin Console

The sync between Azure AD and RealmJoin is scheduled every 15 minutes and based on your custom pattern ruleset.

## Does RealmJoin support Multi-User Devices?

Yes. Starting with version 4.13 RealmJoin allows applications to be installed not only for the primary device user but also for secondary users. See our [Multi-User Devices article](dem-account.md) for more details.

## How to enter the Debug Mode in RealmJoin client?

Press and hold **Strg** + **Shift** and click the RealmJoin icon in the taskbar.  
For a detailed description of **Debug mode** see our [Troubleshooting](troubleshooting.md).

## I accidentally uninstalled RealmJoin-deployed software using the Windows Apps control

Force reinstall by using the **debug mode**. After opening the tray in debug mode, you can find all available software, even if assigned hidden or already installed and rerun the package.

## Can I get rid of Bloatware using RealmJoin?

TBD 

## Is RealmJoin providing an uninstall of software?

A general uninstall feature is currently not implemented. In a 100% modern workplace environment with evergreen applications, regular removable of installed software does not exist anymore.  
Chocolatey packages provide a generic uninstall component that would be usable for RealmJoin.  
But because of the volatile history of unattended and the sometimes unpredictable issues with incomplete uninstalls we have decided against using it.

There are typically three reasons to uninstall software:

* The license should be re-used for a different user. In this case, it's easy to just create a package to enable/disable a license for a user.
* The software needs to be removed because of \[choose your reason\]. In this situation, a dedicated remove-software-package can be created.
* There is a newer version of the software. This is not a reason to use an uninstall command but instead, it is a common practice for every software package used by RealmJoin to 'clean' any precursory binaries or settings.

All items above describe special usecases and should be solved in cooperation with Glück & Kanja Consulting AG.Should I use the applications internal auto-updater or not?

This highly depends on the application itself as well as your internal processes. For some applications, that might be prone to attacking and are very well maintained by the vendor - like Google Chrome - we recommend to use the applications internal update. For other software, it might be more useful to include a regular update via RealmJoin into your processes.

## Re-Install failed software installations

RealmJoin tries to restart failed installations according to your selected installation phases. To reinstall the package manually please use the **Debug Mode** of the RealmJoin agent.

## Since the packages are based on open protocols, can others access my packages?

Yes. NuGet and Chocolatey repositories are based on open protocols. Using search commands one is able to find all repositories that are hosted on the GK tenant. Since packages **should not** contain personalized information like licenses or user-specific data, there is no potential harm in e.g. installing an Office package with a different company name in the package description.  
It is in principle possible to host the RealmJoin

## What firewall/proxy settings do I have to configure?

Please check the [infrastructure requirements](infrastructure.md) for detailed information on the RealmJoin connections.

## Does G&K have any recommendations on workflows?

Yes. Our suggestions can be found in the **workflow** section of this documentation.

## What is the recommendation for reporting?

See section [**States** ](rj-portal/clients.md#states)in the [RealmJoin Portal - Clients article](rj-portal/#clients). It is possible to get virtually any information from each client in JSON-form. There are several applications available to evaluate the data, for example, PowerBI, which allows to sort and process the data in logical and visually pleasing ways.

## In the future, may RealmJoin packages be used in Intune?

If in the future, Microsoft Intune becomes more capable and the installation of software is as versatile and organized as with RealmJoin, you may use the existing packages in Intune. Since RealmJoin does only need Chocolatey and PowerShell to run the installers, there might be possibilities to use Intune to install the software.

All packages created by the Glück & Kanja Consulting AG Package Factory can be prepared as .intunewin packages.

## Is RealmJoin GDPR compliant?

Glück & Kanja takes data protection very seriously. All contracts with customers and partners consider data protection.

## Does the RealmJoin BitLocker enforcement work on virtual machines?

For virtual machines, the encryption is only enforced if the virtual machine variable $env:RjDisableVmDetection=1 is set.  
This setting can be bypassed in the OOBE screen with the command `setx /m RjDisableVmDetection 1` in a cmd shell.

## Is it possible to see the code of store applications?

It is possible to request reading rights for a specific application package from Glück & Kanja. The installation script of already installed packages can be found under `$env:ProgramData\chocolatey\lib\<packageId>\Tools`

## Can I force the weblinks in the RealmJoin tray to use a specific process?

Yes. To do so, the target has to be set to the process and optional args can be provided. Additionally, for edge, the protocol handler can be used:

* Key: "WebLinks" \(directing to process\):

```javascript
   {
"Name": "Citrix-Applikationen",
"Target": "iexplore",
"Args": "https://url.net",
"Platform": "any"
},
{
"Name": "Citrix-Applikationen",
"Target": "microsoft-edge:https://url.net",
"Platform": "any"
}
```

See chapter [Settings and Policies]() for further information.

