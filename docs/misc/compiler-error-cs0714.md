---
title: "编译器错误 CS0714 | Microsoft Docs"
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
  - "CS0714"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0714"
ms.assetid: fbb5dc55-645c-4980-bf4b-3c2f84a3c6cd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0714
“static type”：静态类不能实现接口  
  
 接口可能会在对象上定义非静态方法，因此将不能由静态类实现。 若要解决此错误，请确保你的类不尝试实现任何接口。  
  
## 示例  
 以下示例生成 CS0714：  
  
```  
// CS0714.cs interface I { } public static class C : I  // CS0714 { public static void Main() { } }  
```