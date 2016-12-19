---
title: "需要对程序集“&lt;assemblyname&gt;”(包含实现的接口“&lt;interfacename&gt;”)的引用 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30009"
  - "bc30009"
helpviewer_keywords: 
  - "BC30009"
ms.assetid: b2dfb89d-7fde-4a8e-ba7f-fe1e59eabaca
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 需要对程序集“&lt;assemblyname&gt;”(包含实现的接口“&lt;interfacename&gt;”)的引用
需要对程序集“\<assemblyname\>”\(包含实现的接口“\<interfacename\>”\)的引用。 请向项目中添加一个。  
  
 在动态链接库 \(DLL\) 中或在你项目中没有直接引用的程序集中定义此接口。 如果接口在多个 DLL 或程序集中定义，则 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 编译器需要引用以避免多义性。  
  
 **错误 ID：**BC30009  
  
### 更正此错误  
  
-   将未引用的 DLL 或程序集名称包括在项目引用中。  
  
## 请参阅  
 [NIB：引用命名空间和组件](http://msdn.microsoft.com/zh-cn/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [有关无效的引用的疑难解答](../Topic/Troubleshooting%20Broken%20References.md)