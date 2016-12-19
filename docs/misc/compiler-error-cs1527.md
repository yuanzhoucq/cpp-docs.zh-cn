---
title: "编译器错误 CS1527 | Microsoft Docs"
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
  - "CS1527"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1527"
ms.assetid: a0d52130-d6da-41bb-b153-8e96cbb7e316
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1527
命名空间中定义的元素无法显式声明为 private、protected 或 protected internal  
  
 命名空间中的类型声明可以具有[公共](../Topic/public%20\(C%23%20Reference\).md)或[内部](../Topic/internal%20\(C%23%20Reference\).md)访问。 如果未指定任何可访问性，则默认设置为**内部**。  
  
 以下示例生成 CS1527：  
  
```  
// CS1527.cs namespace Sample { private class C1 {};             // CS1527 protected class C2 {};           // CS1527 protected internal class C3 {};  // CS1527 }  
```  
  
 以下示例将生成 CS1527，因为当程序代码中没有显式声明命名空间时，所有类型声明均隐式存在于全局命名空间内。  
  
```  
//cs1527_2.cs using System; protected class C4{} private struct S1{}  
```  
  
## 请参阅  
 [命名空间](../Topic/Namespaces%20\(C%23%20Programming%20Guide\).md)   
 [global](../Topic/global%20\(C%23%20Reference\).md)   
 [:: 运算符](../Topic/::%20Operator%20\(C%23%20Reference\).md)   
 [可访问域](../Topic/Accessibility%20Domain%20\(C%23%20Reference\).md)   
 [访问修饰符](../Topic/Access%20Modifiers%20\(C%23%20Programming%20Guide\).md)