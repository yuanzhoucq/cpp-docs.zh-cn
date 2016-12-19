---
title: "编译器错误 CS0264 | Microsoft Docs"
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
  - "CS0264"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0264"
ms.assetid: a8a87185-5915-4b0d-a8cd-2f129ea51b8f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0264
“type”的分部声明必须具有顺序相同的相同类型形参名  
  
 如果在分部声明中定义泛型类型，而类型形参的名称或顺序不在所有分部声明中一致，将出现此错误。 要消除此错误，请检查每个分部声明的类型形参，确保使用了形参的相同名称和顺序。 有关详细信息，请参阅[分部类和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)和[泛型类型参数](../Topic/Generic%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)。  
  
## 示例  
 下面的示例生成 CS0264。  
  
```  
// CS0264.cs partial class MyClass<T>  // CS0264 { } partial class MyClass <MyType> { }  
```