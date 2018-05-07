---
title: 编译器错误 C2270 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2270
dev_langs:
- C++
helpviewer_keywords:
- C2270
ms.assetid: b52c068e-0b61-42e7-b775-4d57b3ddcba0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bbafbf35f2aed6d6bddc3298ecfe0e1bf9912e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2270"></a>编译器错误 C2270
function： 非成员函数上不允许的修饰符  
  
 使用声明非成员函数[const](../../cpp/const-cpp.md)，[易失性](../../cpp/volatile-cpp.md)，或另一个内存模型修饰符。  
  
 下面的示例生成 C2270:  
  
```  
// C2270.cpp  
// compile with: /c  
void func1(void) const;   // C2270, nonmember function  
  
void func2(void);  
  
class CMyClass {  
public:  
   void func2(void) const;  
};  
```