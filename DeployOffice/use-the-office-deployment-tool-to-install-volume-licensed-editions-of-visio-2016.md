---
title: "Use the Office Deployment Tool to install volume licensed versions of Project 2016 and Visio 2016"
ms.author: danbrown
author: DHB-MSFT
manager: laurawi
ms.audience: ITPro
ms.topic: get-started-article
ms.service: o365-proplus-itpro
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_ProPlus
ms.custom: Ent_Office_ProPlus
description: "Provides Office admins with information about how to install volume licensed versions of Project 2016 and Visio 2016 on the same computer with Office 365 ProPlus by using the Office Deployment Tool."
---

# Use the Office Deployment Tool to install volume licensed versions of Project 2016 and Visio 2016 

Usually you deploy volume licensed versions of Project 2016 and Visio 2016 by using the Windows Installer (MSI) installation technology. But that won't work if you're trying to install volume licensed versions of Project 2016 and Visio 2016 on the same computer as Office 365 ProPlus. That's because Office 365 ProPlus uses Click-to-Run as its installation technology, and in this case, having MSI and Click-to-Run installations on the same computer isn't supported.

To help you deploy volume licensed versions of Project 2016 and Visio 2016 on the same computer as Office 365 ProPlus, we've provided an alternative installation method: you can use the Office Deployment Tool to do the installation of Project and Visio. The Office Deployment Tool uses Click-to-Run to do the installation, instead of using Windows Installer (MSI). But, Project and Visio are still activated by volume activation methods, such as [Key Management Service (KMS)](vlactivation/activate-office-by-using-kms.md) or [Multiple Activation Key (MAK)](vlactivation/activate-office-by-using-mak.md). 

> [!IMPORTANT]
> - MAK keys that you use for Windows Installer (MSI) installations of Project and Visio won't work with the Office Deployment Tool. You need a different MAK key to deploy volume licensed versions of Project and Visio with the Office Deployment Tool. To get that MAK key, log into the Volume Licensing Service Center (VLSC) and use the key listed under "C2R-P for use with the Office Deployment Tool." 
> - These steps don't apply to volume licensed versions of Project 2019 and Visio 2019. For more information about deploying volume licensed versions of Project 2019 and Visio 2019, see [Deploy Office 2019](office2019/deploy.md).

To begin, [download the most current version](https://go.microsoft.com/fwlink/p/?LinkID=626065) of the Office Deployment Tool from the Microsoft Download Center. Then, edit the Product element in the configuration.xml file, using the appropriate ID from the following table. To use a Generic Volume License Key (GVLK) for volume activation with KMS, use the appropriate value in the table for the PIDKEY attribute.

|**Product**|**ID**|**PIDKEY**|
|:-----|:-----|:-----|
|Project Standard 2016  <br/> |ProjectStdXVolume  <br/> |D8NRQ-JTYM3-7J2DX-646CT-6836M  <br/> |
|Project Professional 2016  <br/> |ProjectProXVolume  <br/> |WGT24-HCNMF-FQ7XH-6M8K7-DRTW9  <br/> |
|Visio Standard 2016  <br/> |VisioStdXVolume  <br/> |NY48V-PPYYH-3F4PX-XJRKJ-W4423  <br/> |
|Visio Professional 2016  <br/> |VisioProXVolume  <br/> |69WXN-MBYV6-22PQG-3WGHK-RM6XC  <br/> |

You can also edit the Updates element in the configuration.xml file to determine how the installation of Project or Visio is updated. For example, you can configure it so that updates are automatically installed from the Office Content Delivery Network (CDN) on the Internet, which is the default, or from a file share on your local network.

If you're not familiar with the Office Deployment Tool, it's usually used to customize deployments of Click-to-Run versions of Office products, such as Office 365 ProPlus. For more information, see [Overview of the Office Deployment Tool](overview-of-the-office-2016-deployment-tool.md). 

Here's an example of a configuration.xml file that can be used to install a 64-bit version of Visio Professional 2016 in English from the Office CDN using a GVLK. 

```xml
<Configuration>
  <Add OfficeClientEdition="64" >
    <Product ID="VisioProXVolume" PIDKEY="69WXN-MBYV6-22PQG-3WGHK-RM6XC">
        <Language ID="en-us" />
     </Product>
   </Add>  
</Configuration>
```

For information about other settings, see [Configuration options for the Office Deployment Tool](configuration-options-for-the-office-2016-deployment-tool.md).

Then, use the Office Deployment Tool to download and install Project or Visio.


## Related topics

- [Supported scenarios for installing different versions of Office, Project, and Visio on the same computer](install-different-office-visio-and-project-versions-on-the-same-computer.md)

