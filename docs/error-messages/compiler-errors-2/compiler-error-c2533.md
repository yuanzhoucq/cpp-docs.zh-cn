---
title: "编译器错误 C2533 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2533
dev_langs:
- C++
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c21849c7318ac4f169bf7104a478fa57ba7dd040
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2533"></a>编译器错误 C2533
“identifier”: 构造函数不能有返回类型  
  
 构造函数不能具有返回类型（甚至不能是 `void` 返回类型）。  
  
 此错误的常见来源是类定义结尾与第一个构造函数实现之间缺少分号。 编译器会将类视为构造函数返回类型的定义，会生成 C2533。  
  
 下面的示例生成 C2533，并演示如何修复此错误：  
  
```  
// C2533.cpp  
// compile with: /c  
class X {  
public:  
   X();     
};  
  
int X::X() {}   // C2533 - constructor return type not allowed  
X::X() {}   // OK - fix by using no return type  
```
