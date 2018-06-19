---
title: 编译器错误 C2355 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2355
dev_langs:
- C++
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b88bf1619a003faa57d1fe1d4f03219267481d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33195719"
---
# <a name="compiler-error-c2355"></a>编译器错误 C2355
“this”：只能在非静态成员函数或非静态数据成员初始值设定项的内部引用  
  
 `this` 指针仅在非静态成员函数或非静态数据成员初始值设定项的内部有效。 当类声明外部的成员函数定义的类范围未正确限定时，可能发生此错误。 当 `this` 指针用于未在类中声明的函数时，也可能发生此错误。  
  
 要解决此问题，请确保成员函数定义与类中的成员函数声明匹配，且未声明为静态。 对于数据成员初始值设定项，请确保数据成员未声明为静态。  
  
 下面的示例生成 C2355，并演示如何修复此错误：  
  
```  
// C2355.cpp  
// compile with: /c  
class MyClass {};  
MyClass *p = this;   // C2355  
  
// OK  
class MyClass2 {  
public:  
   void Test() {  
      MyClass2 *p = this;  
   }  
};  
```