---
title: "编译器错误 C2803 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2803"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2803"
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2803
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator operator”必须至少有一个类类型的形参  
  
 重载运算符缺少类类型的参数。  
  
 您需要通过引用（不是使用指针，而是使用引用）或值至少传递一个参数，从而能够编写“a \< b”（a 和 b 均为类 A 类型）。  
  
 如果两个参数都是指针，结果将是指针地址的纯比较，并且将不使用用户定义的转换。  
  
 下面的示例生成 C2803：  
  
```  
// C2803.cpp  
// compile with: /c  
class A{};  
bool operator< (const A *left, const A *right);   // C2803  
// try the following line instead  
// bool operator< (const A& left, const A& right);  
```