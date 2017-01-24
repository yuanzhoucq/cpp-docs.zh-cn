---
title: "编译器错误 CS1537 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1537"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1537"
ms.assetid: fdc17f3e-05b3-4d04-8825-4563aec816f5
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1537
using 别名“alias”以前在此命名空间中出现过  
  
 你曾两次将某个符号定义为了命名空间的别名。 一个符号只能定义一次。  
  
 下面的示例生成 CS1537：  
  
```  
// CS1537.cs namespace x { using System; using Object = System.Object; using Object = System.Object;   // CS1537, delete this line to resolve using System = System; }  
```