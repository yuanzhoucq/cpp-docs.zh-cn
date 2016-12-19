---
title: "MSBuild 错误 MSB3117 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.HostInBrowserInvalidFrameworkVersion"
helpviewer_keywords: 
  - "MSB3117"
ms.assetid: 18aec642-6000-4626-bf75-f3547769c780
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3117
**MSB3117: 应用程序设置为以浏览器为宿主，但 TargetFrameworkVersion 设置为 v2.0。**  
  
 部署 WPF Web 浏览器应用程序时将 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> 属性设置为 `True`，但 TargetFrameworkVersion 设置为 `v2.0` 或 `v3.0`。  如果要使用此设置，还必须将 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> 属性设置为 `v3.5` 或更高的值。  
  
### 更正此错误  
  
-   将 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> 属性设置为 `v3.5` 或更高的值。  
  
## 请参阅  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [“项目设计器”\-\>“发布”页](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [MSBuild 错误 MSB3116](../misc/msbuild-error-msb3116.md)   
 [MSBuild 错误 MSB3118](../misc/msbuild-error-msb3118.md)   
 [MSBuild 错误 MSB3174](../misc/msbuild-error-msb3174.md)   
 [MSBuild 错误 MSB3185](../misc/msbuild-error-msb3185.md)