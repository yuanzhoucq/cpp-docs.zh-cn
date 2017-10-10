---
title: "编译器错误 C2803 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2803
dev_langs:
- C++
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: efa9efa2dc204d302f69d873c0199d4431efccb1
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2803"></a>编译器错误 C2803
operator operator 必须具有至少一个类类型的正式参数  
  
 重载的运算符缺少类类型的参数。  
  
 您需要通过引用（不是使用指针，而是使用引用）或值至少传递一个参数，才能够编写“a < b”（a 和 b 均为类 A 类型）。  
  
 如果这两个参数都是指针，它将是指针地址的纯比较，并且将不使用用户定义的转换。  
  
 下面的示例生成 C2803:  
  
```  
// C2803.cpp  
// compile with: /c  
class A{};  
bool operator< (const A *left, const A *right);   // C2803  
// try the following line instead  
// bool operator< (const A& left, const A& right);  
```
