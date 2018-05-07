---
title: 编译器警告 （等级 4） C4256 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4256
dev_langs:
- C++
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed1a40f0da75460c4306f69da0f26eb0888bef66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4256"></a>编译器警告（等级 4）C4256
function:...; 已具有虚拟基的类的构造函数调用可能不兼容与旧版本的 Visual c + +  
  
 可能不兼容。  
  
 请考虑以下代码示例。 如果定义的构造函数 s2:: S2 (int i，...) 使用的版本 7 之前的, Visual c + + 编译器版本编译但下面的示例使用编译的当前版本，对 S3 的构造函数的调用将无法由于正常工作特殊情况调用约定发生了更改。 如果两者都是使用 Visual C++ 6.0 编译的，该调用也无法完全正常工作，除非不为省略号传递任何参数。  
  
 若要修复此警告  
  
1.  请勿在构造函数中使用省略号。  
  
2.  请确保在其项目中的所有组件都生成与当前版本 （包括任何库，可以定义或引用此类），然后禁用警告使用[警告](../../preprocessor/warning.md)杂注。  
  
 下面的示例生成 C4256:  
  
```  
// C4256.cpp  
// compile with: /W4  
// #pragma warning(disable : 4256)  
struct S1  
{  
};  
  
struct S2: virtual public S1  
{  
   S2( int i, ... )    // C4256  
   {  
      i = 0;  
   }  
   /*  
   // try the following line instead  
   S2( int i)  
   {  
      i = 0;  
   }  
   */  
};  
  
void func1()  
{  
   S2 S3( 2, 1, 2 );   // C4256  
   // try the following line instead  
   // S2 S3( 2 );  
}  
  
int main()  
{  
}  
```