---
title: "MSBuild 错误 MSB3125 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsNoEntryPoint"
helpviewer_keywords: 
  - "MSB3125"
ms.assetid: f8a08b05-1946-4788-8577-ceefde785e95
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3125
**MSB3125: 应用程序正在使用文件关联，但没有 EntryPoint 生成参数。**  
  
 没有 entryPoint 生成参数时会发生此错误。  将应用程序配置为使用文件关联时，应用程序清单中必须有一个 entryPoint 生成参数。  \<entryPoint\> 元素标识在应用程序运行时应执行的程序集。  
  
### 更正此错误  
  
-   将 [\<entryPoint\> 元素](../Topic/%3CentryPoint%3E%20Element%20\(ClickOnce%20Application\).md)设置为有效值。  有关更多信息，请参见 [ClickOnce 应用程序清单](../Topic/ClickOnce%20Application%20Manifest.md)。  
  
## 请参阅  
 [“项目设计器”\-\>“发布”页](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [ClickOnce 应用程序清单](../Topic/ClickOnce%20Application%20Manifest.md)