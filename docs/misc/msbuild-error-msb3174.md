---
title: "MSBuild 错误 MSB3174 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.InvalidValue"
helpviewer_keywords: 
  - "MSB3174"
ms.assetid: 6f9a040c-7f21-40fd-bf74-03f99f265e79
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3174
**MSB3174: 无效的“\<file\>”值。**  
  
 当生成过程在检查清单文件格式的过程中遇到常规错误时，便会产生此错误。  错误消息中将包含清单文件名。  
  
 以下任一参数设置不正确均会生成此错误消息。  列出的每个参数均为 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest> 或 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest> 属性，如 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> 或 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.MinimumRequiredVersion%2A>。  
  
 当任务为 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest> 时，下列要求适用：  
  
|Parameter|要求|  
|---------------|--------|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyName%2A>|必须是有效的文件名。|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyVersion%2A>|与 <xref:System.Version.%23ctor%2A> 的要求相同。  所有八位字节都必须大于 0。  必须指定全部四个八位字节。  可以接受空字符串。|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.ClrVersion%2A>|与 <xref:System.Version.%23ctor%2A> 的要求相同。  所有八位字节都必须大于 0。  必须指定全部四个八位字节。  可以接受空字符串。|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.OSVersion%2A>|与 <xref:System.Version.%23ctor%2A> 的要求相同。  所有八位字节都必须大于 0。  必须指定全部四个八位字节。  可以接受空字符串。|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.Platform%2A>|必须为**“AnyCPU”**、**“x86”**、**“x64”**或**“Itanium”**。  可以接受空字符串。|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.ManifestType%2A>|必须为**“Native”**或**“ClickOnce”**。|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.TargetCulture%2A>|可以为空字符串。  也可以为非特定区域性（只能由双字母小写语言代码指定，例如，“jp”代表日语）。  否则，此值的要求与 <xref:System.Globalization.CultureInfo.%23ctor%2A> 的要求相同。|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>|格式必须为 v*\#*.*\#*。  版本必须高于 2.0。  可以接受空字符串。|  
  
 当任务为 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest> 时，下列要求适用：  
  
|Parameter|要求|  
|---------------|--------|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyName%2A>|必须是有效的文件名。|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyVersion%2A>|与 <xref:System.Version.%23ctor%2A> 的要求相同。  所有八位字节都必须大于 0。  必须指定全部四个八位字节。  可以接受空字符串。|  
|<xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.MinimumRequiredVersion%2A>|与 <xref:System.Version.%23ctor%2A> 的要求相同。  所有八位字节都必须大于 0。  可以接受空字符串。|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.Platform%2A>|必须为**“AnyCPU”**、**“x86”**、**“x64”**或**“Itanium”**。  可以接受空字符串。|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.TargetCulture%2A>|可以为空字符串。  也可以为非特定区域性（只能由双字母小写语言代码指定，例如，“jp”代表日语）。  否则，此值的要求与 <xref:System.Globalization.CultureInfo.%23ctor%2A> 的要求相同。|  
|<xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.UpdateMode%2A>|必须为**“前台”**或**“后台”**。  可以接受空字符串。|  
|<xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.UpdateUnit%2A>|必须为**“小时”**、**“天”**或**“星期”**。  可以接受空字符串。|  
  
## 请参阅  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [产品和包架构引用](../Topic/Product%20and%20Package%20Schema%20Reference.md)   
 [“项目设计器”\-\>“发布”页](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [MSBuild 错误 MSB3116](../misc/msbuild-error-msb3116.md)   
 [MSBuild 错误 MSB3117](../misc/msbuild-error-msb3117.md)   
 [MSBuild 错误 MSB3118](../misc/msbuild-error-msb3118.md)   
 [MSBuild 错误 MSB3185](../misc/msbuild-error-msb3185.md)