---
title: "MSBuild 错误 MSB3153 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageValidation"
helpviewer_keywords: 
  - "MSB3153"
ms.assetid: 937bb1ff-79f7-45a5-a085-525f4b48ea4e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3153
**MSB3153: 位于“\<folder\>”的项“\<package\>”未通过 Xml 验证。**  
  
 此警告在清单（具体为 package.xml）未通过 XML 验证时产生。  具体问题在后续错误消息（[MSBuild 错误 MSB3159](../misc/msbuild-error-msb3159.md) 或 [MSBuild 错误 MSB3160](../misc/msbuild-error-msb3160.md)）中列出。  
  
### 更正此错误  
  
-   解决后续错误消息中列出的清单验证问题。  
  
## 请参阅  
 [产品和包架构引用](../Topic/Product%20and%20Package%20Schema%20Reference.md)   
 [\<PackageFiles\> 元素](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)