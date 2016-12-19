---
title: "编译器错误 CS1925 | Microsoft Docs"
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
  - "CS1925"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1925"
ms.assetid: b60806a5-2ccf-47f5-873b-7ac2292fdb54
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1925
无法使用集合初始值设定项初始化类型“type”的对象  
  
 集合初始值设定项仅允许用于满足特定条件的集合类。 有关更多信息，请参见[对象和集合初始值设定项](../Topic/Object%20and%20Collection%20Initializers%20\(C%23%20Programming%20Guide\).md)。 尝试使用嵌套在集合初始值设定项中的数组初始值设定项的缩写形式时，也会产生此错误。  
  
### 更正此错误  
  
1.  通过调用对象的构造函数和方法将对象初始化。  
  
## 示例  
 以下代码生成 CS1925：  
  
```  
// cs1925.cs public class Student { public int[] Scores; } class Test { static void Main(string[] args) { Student student = new Student { Scores = { 1, 2, 3 } }; // CS1925 } }  
```