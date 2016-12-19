---
title: "编译器错误 CS0315 | Microsoft Docs"
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
  - "CS0315"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0315"
ms.assetid: 9bb1cab3-1dca-4467-978b-1ab310901a70
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0315
不能将类型“valueType”用作泛型类型或方法“TypeorMethod\<T\>”中的类型形参“T”。 没有从“valueType”到“referenceType”的装箱转换。  
  
 将泛型类型约束为特定类，并尝试使用不能隐式装箱到它的值类型构造该类的实例时，会发生此错误。  
  
### 更正此错误  
  
1.  一种解决方案是将结构重新定义为类。  
  
## 示例  
 下面的示例生成 CS0315：  
  
```  
// cs0315.cs public class ClassConstraint { } public struct ViolateClassConstraint { } public class Gen<T> where T : ClassConstraint { } public class Test { public static int Main() { Gen<ViolateClassConstraint> g = new Gen<ViolateClassConstraint>(); //CS0315 return 1; } }  
```  
  
## 请参阅  
 [类型参数的约束](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)   
 [装箱和取消装箱](../Topic/Boxing%20and%20Unboxing%20\(C%23%20Programming%20Guide\).md)