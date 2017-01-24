---
title: "编译器错误 CS1959 | Microsoft Docs"
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
  - "CS1959"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1959"
ms.assetid: 20a31619-3e30-446a-becc-a7f8cfcec66d
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1959
“name”属于类型“type”。 在常量声明中指定的类型必须为 sbyte、byte、short、ushort、int、uint、long、ulong、char、float、double、decimal、bool、string、枚举类型或引用类型。  
  
 常数声明中允许的类型仅限于此消息中描述的类型。  
  
### 更正此错误  
  
1.  声明具有允许类型的常量。  
  
## 示例  
 以下代码会产生 CS1959，因为 `null` 不是类型。  
  
```  
// cs1959.cs class Program { static void Test<T>() where T : class { const T x = null; // CS1959 } }  
```  
  
## 请参阅  
 [常量](../Topic/Constants%20\(C%23%20Programming%20Guide\).md)   
 [null](../Topic/null%20\(C%23%20Reference\).md)