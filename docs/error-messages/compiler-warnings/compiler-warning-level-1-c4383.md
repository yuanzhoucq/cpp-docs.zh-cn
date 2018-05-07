---
title: 编译器警告 （等级 1） C4383 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4383
dev_langs:
- C++
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b78209cf4e3e320cca8b161a4e6c99eaca6d771c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4383"></a>编译器警告（等级 1）C4383
instance_dereference_operator： 取消句柄引用的含义可以时的用户定义 operator 运算符存在; 更改编写作为静态函数进行显式有关操作数的运算符  
  
 托管类型中添加取消引用运算符的用户定义的实例重写时，可能会重写的类型的取消引用运算符返回的句柄的对象的功能。 请考虑编写用户定义的一个静态取消引用运算符。  
  
 有关详细信息，请参阅[对象句柄运算符 (^)](../../windows/handle-to-object-operator-hat-cpp-component-extensions.md)和[跟踪引用运算符](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
 此外，实例运算符不可用于其他语言编译器通过引用的元数据。 有关详细信息，请参阅[用户定义的运算符 (C + + /cli CLI)](../../dotnet/user-defined-operators-cpp-cli.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4383。  
  
```  
// C4383.cpp  
// compile with: /clr /W1  
  
ref struct S {  
   int operator*() { return 0; }   // C4383  
};  
  
ref struct T {  
   static int operator*(T%) { return 0; }  
};   
  
int main() {  
   S s;  
   S^ pS = %s;  
  
   T t;  
   T^ pT = %t;  
   T% rT = *pT;  
}  
```