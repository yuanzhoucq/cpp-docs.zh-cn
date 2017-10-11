---
title: "编译器错误 C2723 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2723
dev_langs:
- C++
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 3816640569a503c8a56c4cf37f1bf23360b30a12
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2723"></a>编译器错误 C2723
“函数”：“specifier”说明符在函数定义上非法  
  
 说明符不能与类声明外部的函数定义同时出现。 仅能对类声明内的成员函数声明指定 `virtual` 说明符。  
  
 下面的示例生成 C2723 并显示如何修复它：  
  
```  
// C2723.cpp  
struct X {  
   virtual void f();  
   virtual void g();  
};  
  
virtual void X::f() {}   // C2723  
  
// try the following line instead  
void X::g() {}  
```
