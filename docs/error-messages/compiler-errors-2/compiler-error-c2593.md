---
title: "编译器错误 C2593 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2593
dev_langs:
- C++
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: cb0b752259503f7e14cd78298e487f5304e13a0d
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2593"></a>编译器错误 C2593
运算符 identifier 不明确  
  
 为重载运算符定义了多个可能的运算符。  
  
 如果上一个或多个实际参数使用显式强制转换，则可能会修复此错误。  
  
 下面的示例生成 C2593:  
  
```  
// C2593.cpp  
struct A {};  
struct B : A {};  
struct X {};  
struct D : B, X {};  
void operator+( X, X );  
void operator+( A, B );  
D d;  
  
int main() {  
   d +  d;         // C2593, D has an A, B, and X   
   (X)d + (X)d;    // OK, uses operator+( X, X )  
}  
```  
  
 此错误可能由序列化浮点变量 using`CArchive`对象。 编译器标识`<<`为不明确的运算符。 仅基元 c + + 类型`CArchive`可以序列化是固定大小类型`BYTE`， `WORD`， `DWORD`，和`LONG`。 用于序列化，所有的整数类型必须转换为这些类型之一。 必须使用存档浮点类型`CArchive::Write()`成员函数。  
  
 下面的示例演示如何存档浮点变量 (`f`) 到存档`ar`:  
  
```  
ar.Write(&f, sizeof( float ));  
```
