---
title: "编译器错误 CS1059 | Microsoft Docs"
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
  - "CS1059"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1059"
ms.assetid: 3ebd02ab-e40d-4aad-b901-a0cb6e2eace7
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1059
递增运算符或递减运算符的操作数必须是变量、属性或索引器。  
  
 在尝试递增或递减常量值时，会引发此错误。 如果尝试递增表达式（如 `(a+b)++`），也会发生此错误。  
  
### 更正此错误  
  
-   使变量成为非常量变量。  
  
-   删除递增或递减运算符。  
  
-   将表达式存储在一个变量中，然后递增该变量。  
  
## 示例  
 下面的示例生成 CS1059，因为 `i` 是常量而非变量，并且 `E` 为 `Enum` 类型，该类型的元素也是常量值。  
  
```  
// CS1059.cs class Program { public enum E : sbyte { a = 1, b = 2 } static void Main(string[] args) { const int i = 0; i++;            // CS1059 E test = E.a++; // CS1059 } }  
```  
  
## 请参阅  
 [常量](../Topic/Constants%20\(C%23%20Programming%20Guide\).md)