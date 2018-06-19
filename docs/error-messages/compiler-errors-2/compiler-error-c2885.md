---
title: 编译器错误 C2885 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2885
dev_langs:
- C++
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f37ea0f9fadb74b44eea5ad110f7f12b884f0e41
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244167"
---
# <a name="compiler-error-c2885"></a>编译器错误 C2885
class::identifier： 不使用的声明无效非类范围内  
  
 你使用[使用](../../cpp/using-declaration.md)声明不正确。  
  
## <a name="example"></a>示例  
 此错误可能来自于为 Visual c + + 2005年执行的编译器一致性工作： 不再有效能够`using`声明嵌套的类型，则必须显式限定对嵌套类型，将类型放在名称中所做的每个引用空间，或创建一个 typedef。  
  
 下面的示例生成 C2885。  
  
```  
// C2885.cpp  
namespace MyNamespace {  
   class X1 {};  
}  
  
struct MyStruct {  
   struct X1 {  
      int i;  
   };  
};  
  
int main () {  
   using MyStruct::X1;   // C2885  
  
   // OK  
   using MyNamespace::X1;  
   X1 myX1;  
  
   MyStruct::X1 X12;  
  
   typedef MyStruct::X1 abc;  
   abc X13;  
   X13.i = 9;  
}  
```  
  
## <a name="example"></a>示例  
 如果你使用`using`关键字后的跟类成员，c + + 需要定义该成员在其他类 （派生类）。  
  
 下面的示例生成 C2885。  
  
```  
// C2885_b.cpp  
// compile with: /c  
class A {  
public:  
   int i;  
};  
  
void z() {  
   using A::i;   // C2885 not in a class  
}  
  
class B : public A {  
public:  
   using A::i;  
};  
```