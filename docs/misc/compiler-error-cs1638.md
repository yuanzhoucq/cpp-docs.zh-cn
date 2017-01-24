---
title: "编译器错误 CS1638 | Microsoft Docs"
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
  - "CS1638"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1638"
ms.assetid: 5279c060-5be3-4c29-80cc-21326d4cffdb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1638
“identifier”是保留的标识符，并且不能在使用 ISO 语言版本模式时使用  
  
 当 **\/langversion** 编译器开关指定了 ISO 语言兼容性选项时，在标识符中任意位置具有双下划线的任何标识符都将造成此错误。 若要避免此错误，请消除任何带双下划线的标识符或不使用 ISO\-1 语言版本选项。  
  
## 示例  
 下面的示例生成 CS1638：  
  
```  
// CS1638.cs // compile with: /langversion:ISO-1 class bad__identifer // CS1638 (double underscores are not ISO compliant) { } // Try this instead: //class GoodIdentifier //{ //} class CMain { public static void Main() { } }  
```  
  
## 请参阅  
 [\/langversion \(Conformant Syntax\)](../Topic/-langversion%20\(C%23%20Compiler%20Options\).md)