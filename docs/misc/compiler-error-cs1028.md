---
title: "编译器错误 CS1028 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1028"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1028"
ms.assetid: 9df07db3-256f-45e9-8323-26539c55a1d8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1028
意外的预处理器指令  
  
 已发现一个意外的[预处理器指令](../Topic/C%23%20Preprocessor%20Directives.md)。  
  
 例如，`#endif` 前面没有找到 `#if`。  
  
 以下示例生成 CS1028：  
  
```  
// CS1028.cs #endif   // CS1028, no matching #if namespace x { public class clx { public static void Main() { } } }  
```