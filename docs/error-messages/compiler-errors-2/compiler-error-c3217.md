---
title: "编译器错误 C3217 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3217"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3217"
ms.assetid: 99070417-c23a-4d82-bdd2-04be1a07adea
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3217
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“param”: 泛型参数不能在此声明中进行约束  
  
 约束的格式错误；约束泛型参数必须与泛型类模板参数一致。  
  
 下面的示例生成 C3217：  
  
```  
// C3217.cpp // compile with: /clr interface struct A {}; generic <class T> ref class C { generic <class T1> where T : A   // C3217 void f(); };  
```  
  
 以下示例演示了可能的解决方法：  
  
```  
// C3217b.cpp // compile with: /clr /c interface struct A {}; generic <class T> ref class C { generic <class T1> where T1 : A void f(); };  
```