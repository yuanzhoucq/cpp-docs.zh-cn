---
title: 编译器错误 C3073 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3073
dev_langs:
- C++
helpviewer_keywords:
- C3073
ms.assetid: b24b9b8b-f9fb-4c3c-a1a0-97fad2081bfc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f565973c386dbaa9c1146756e7ca1b1f75f4b43b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253611"
---
# <a name="compiler-error-c3073"></a>编译器错误 C3073
type: ref 类没有用户定义的复制构造函数  
  
 在[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)编译，编译器不会生成引用类型的复制构造函数。 在任何 **/clr**编译，你必须定义你自己对于引用类型的复制构造函数如果你预计要复制的类型的实例。  
  
 有关详细信息，请参阅[对于引用类型的 c + + 堆栈语义](../../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3073。  
  
```  
// C3073.cpp  
// compile with: /clr  
ref class R {  
public:  
   R(int) {}  
};  
  
ref class S {  
public:  
   S(int) {}  
   S(const S %rhs) {}   // copy constructor  
};  
  
void f(R) {}  
void f2(S) {}  
void f3(R%){}  
  
int main() {  
   R r(1);  
   f(r);   // C3073  
   f3(r);   // OK  
  
   S s(1);  
   f2(s);   // OK  
}  
```