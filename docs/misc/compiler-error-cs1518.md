---
title: "编译器错误 CS1518 | Microsoft Docs"
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
  - "CS1518"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1518"
ms.assetid: 26e0870d-fe91-4c66-b3f8-ed2b074c964e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1518
应输入 class、delegate、enum、interface 或 struct  
  
 找到在[命名空间](../Topic/namespace%20\(C%23%20Reference\).md)中不受支持的声明。 在命名空间中，编译器仅接受类、结构、枚举、接口、命名空间和委托。  
  
## 示例  
 下面的示例生成 CS1518：  
  
```  
// CS1518.cs namespace x { sealed class c1 {};      // OK namespace f2 {};         // OK sealed f3 {};            // CS1518 }  
```