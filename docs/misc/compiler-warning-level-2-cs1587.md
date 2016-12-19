---
title: "编译器警告（等级 2）CS1587 | Microsoft Docs"
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
  - "CS1587"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1587"
ms.assetid: b27c2009-d485-43fd-a649-fbc15570d256
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器警告（等级 2）CS1587
XML 注释没有放在有效语言元素上  
  
 建议用于文档注释的标记不能用于所有语言元素。 例如，命名空间上不允许标记。 有关 XML 注释的详细信息，请参阅[建议的文档注释标记](../Topic/Recommended%20Tags%20for%20Documentation%20Comments%20\(C%23%20Programming%20Guide\).md)。  
  
## 示例  
 下面的示例生成 CS1587：  
  
```  
// CS1587.cs // compile with: /W:2 /doc:x.xml /// <summary>test</summary>   // CS1587, tag not allowed on namespace namespace MySpace { class MyClass { public static void Main() { } } }  
```