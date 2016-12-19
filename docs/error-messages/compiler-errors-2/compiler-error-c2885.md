---
title: "编译器错误 C2885 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2885"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2885"
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2885
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class::identifier”: 在非类范围内不是有效的 using 声明  
  
 错误地使用了 [using](../../cpp/using-declaration.md) 声明。  
  
## 示例  
 为 Visual C\+\+ 2005 执行的编译器一致性工作可能导致此错误：对嵌套类型使用 `using` 声明不再有效；必须显式限定对嵌套类型的每个引用、将类型放入命名空间或创建 typedef。  
  
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
  
## 示例  
 如果将 `using` 关键字与类成员一起使用，则 C\+\+ 要求在另一个类（派生类）的内部定义该成员。  
  
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