---
title: "编译器错误 C3379 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3379"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3379"
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C3379
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: 嵌套类不能将程序集访问说明符作为声明的一部分  
  
 应用于托管类型（如类或结构）时，[public](../../cpp/public-cpp.md) 和 [private](../../cpp/private-cpp.md) 关键字指示该类是否将通过程序集元数据公开。  `public` 或 `private` 不能应用于嵌套类，嵌套类将继承对封闭类的程序集访问。  
  
 与 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 一起使用时，`ref` 和 `value` 关键字指示该类是托管类（请参见 [类和结构 \(托管\)](../../windows/classes-and-structs-cpp-component-extensions.md)）。  
  
 下面的示例生成 C3379：  
  
```  
// C3379a.cpp  
// compile with: /clr  
using namespace System;  
  
public ref class A {  
public:  
   static int i = 9;  
  
   public ref class BA {   // C3379  
   // try the following line instead  
   // ref class BA {  
   public:  
      static int ii = 8;  
   };  
};  
  
int main() {  
  
   A^ myA = gcnew A;  
   Console::WriteLine(myA->i);  
  
   A::BA^ myBA = gcnew A::BA;  
   Console::WriteLine(myBA->ii);  
}  
```  
  
 下面的示例生成 C3379：  
  
```  
// C3379b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
public __gc class A {  
public:  
   static int i = 9;  
  
   public __gc class BA {   // C3379  
   // try the following line instead  
   // __gc class BA {  
   public:  
      static int ii = 8;  
   };  
};  
  
int main() {  
  
   A *myA = new A;  
   Console::WriteLine(myA->i);  
  
   A::BA *myBA = new A::BA;  
   Console::WriteLine(myBA->ii);  
}  
```