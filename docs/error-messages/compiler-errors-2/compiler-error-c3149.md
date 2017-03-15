---
title: "编译器错误 C3149 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3149
dev_langs:
- C++
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: 555b3a7ac8e0d1e5de8eacd763c9ee63101e5b78
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3149"></a>编译器错误 C3149
type︰ 不能使用不顶级 char 的情况下此类型  
  
 未正确指定一个声明。  
  
 例如，您可能会定义在全局范围内的 CLR 类型并尝试作为定义的一部分创建类型的变量。 因为不允许使用 CLR 类型的全局变量，则编译器将生成 C3149。  
  
 若要解决此错误，声明函数或类型定义内的 CLR 类型的变量。  
  
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

