---
title: 编译器错误 C2597 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2597
dev_langs:
- C++
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45cf9054736117526ee5e79c0bafdd8fdee7c2e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229345"
---
# <a name="compiler-error-c2597"></a>编译器错误 C2597
对非静态成员“identifier”的非法引用  
  
 可能的原因：  
  
1.  在静态成员函数中指定了非静态成员。 若要访问非静态成员，必须传入或创建类的本地实例并使用成员访问运算符（`.` 或 `->`）。  
  
2.  指定标识符不是类、结构或联合的成员。 检查标识符拼写。  
  
3.  成员访问运算符引用非成员函数。  
  
4.  下面的示例生成 C2597，并演示如何修复此错误：  
  
```  
// C2597.cpp  
// compile with: /c  
struct s1 {  
   static void func();  
   static void func2(s1&);  
   int i;  
};  
  
void s1::func() {  
   i = 1;    // C2597 - static function can't access non-static data member  
}  
  
// OK - fix by passing an instance of s1  
void s1::func2(s1& a) {  
   a.i = 1;  
}  
```