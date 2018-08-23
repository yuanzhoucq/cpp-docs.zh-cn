---
title: 编译器错误 C3149 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3149
dev_langs:
- C++
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c0441a7aebf86139aedbd5e45a7645db0a90b37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248503"
---
# <a name="compiler-error-c3149"></a>编译器错误 C3149
type： 不能使用不顶级 char 的情况下此类型  
  
 声明未正确指定。  
  
 例如，你可能具有定义在全局范围内的 CLR 类型并尝试作为定义的一部分创建的变量的类型。 因为不允许的 CLR 类型的全局变量，编译器将生成 C3149。  
  
 若要解决此错误，声明一个函数或类型定义中的 CLR 类型的变量。  
  
 下面的示例生成 C3149:  
  
```  
// C3149.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   // declare an array of value types   
   array< Int32 ^> IntArray;   // C3149  
   array< Int32>^ IntArray2;   // OK  
}  
```  
  
 下面的示例生成 C3149:  
  
```  
// C3149b.cpp  
// compile with: /clr /c  
delegate int MyDelegate(const int, int);  
void Test1(MyDelegate m) {}   // C3149  
void Test2(MyDelegate ^ m) {}   // OK  
```  
