---
title: "MSBuild 错误 MSB3122 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsApplicationNotFullTrust"
helpviewer_keywords: 
  - "MSB3122"
ms.assetid: 523e4160-f165-437a-9f19-fb2ec77d46f5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3122
**MSB3122: 使用文件关联需要完全信任。**  
  
 发布配置文件关联的应用程序要求该应用程序为完全可信应用程序。  
  
### 更正此错误  
  
-   启用 ClickOnce 安全设置，并将应用程序设置为完全可信应用程序。  有关更多信息，请参见[如何：启用 ClickOnce 安全设置](../Topic/How%20to:%20Enable%20ClickOnce%20Security%20Settings.md)。  
  
## 请参阅  
 [“项目设计器”\-\>“发布”页](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [ClickOnce 应用程序清单](../Topic/ClickOnce%20Application%20Manifest.md)   
 [ClickOnce 应用程序的代码访问安全性](../Topic/Code%20Access%20Security%20for%20ClickOnce%20Applications.md)