---
title: 编译器错误 C3243 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3243
dev_langs:
- C++
helpviewer_keywords:
- C3243
ms.assetid: 35d8ad1a-377d-47df-be9d-c55eea23340f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3dce7b5ed4681e8624869fe25b713cf6646366f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3243"></a>编译器错误 C3243
“interface”未引入任何重载函数  
  
 你试图 [显式重写](../../cpp/explicit-overrides-cpp.md) 在指定接口中不存在的成员。  
  
 下面的示例生成 C3243：  
  
```  
// C3243.cpp  
#pragma warning(disable:4199)  
__interface IX14A {  
   void g();  
};  
  
__interface IX14B {  
   void f();  
   void f(int);  
};  
  
class CX14 : public IX14A, public IX14B {  
public:  
   void IX14A::g();  
   void IX14B::f();  
   void IX14B::f(int);  
};  
  
void CX14::IX14A::f()   // C3243 occurs here  
{  
}  
```