---
title: "编译器错误 CS1103 | Microsoft Docs"
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
  - "CS1103"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1103"
ms.assetid: 513a26ea-9d66-4dc3-b3e6-d709c3089b1a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1103
扩展方法的第一个参数的类型不能是“type”。  
  
 扩展方法的第一个参数的类型不能是指针类型。  
  
## 示例  
 下面的示例生成 CS1103：  
  
```  
// cs1103.cs public static class Extensions { public unsafe static char* Test(this char* charP) { return charP; } // CS1103 }   
```  
  
## 请参阅  
 [扩展方法](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [unsafe](../Topic/unsafe%20\(C%23%20Reference\).md)