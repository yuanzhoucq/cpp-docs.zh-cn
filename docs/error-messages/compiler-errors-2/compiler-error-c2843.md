---
title: "编译器错误 C2843 | Microsoft Docs"
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
  - "C2843"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2843"
ms.assetid: 9d3f2ac4-eea5-4fed-abeb-e752f442bfcc
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2843
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”：不能获取托管或 WinRT 类型的非静态数据成员或方法的地址  
  
 需要实例才能获取托管或 WinRT 类或接口的非静态数据成员的地址。  
  
 下面的示例生成 C2843，并介绍了如何修复此错误：  
  
```  
// C2843_2.cpp  
// compile with: /clr  
public ref class C {  
public:  
   int m_i;  
};  
  
ref struct MyStruct {  
   static void sf() {}  
   void f() {}  
};  
  
int main() {  
   MyStruct ^ps = gcnew MyStruct;  
   void (__clrcall MyStruct::*F1)() = & MyStruct::f;   // C2843  
   void (__clrcall MyStruct::*F2)() = & ps->f;   // C2843  
   void (__clrcall MyStruct::*F3)();   // C2843  
  
   void (__clrcall *F5)() = MyStruct::sf;   // OK  
   void (__clrcall *F6)() = & ps->sf;   // OK  
  
   interior_ptr<int> i = &C::m_i; // C2843  
   C ^x = gcnew C();  
   interior_ptr<int> ii = &x->m_i;  
}  
```  
  
 下面的示例生成 C2843，并介绍了如何修复此错误：  
  
```  
// C2843.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
public __gc class C {  
public:  
   int m_i;  
};  
  
__gc struct MyStruct {  
   static void sf() {}  
   void f() {}  
};  
  
int main() {  
   MyStruct *ps = new MyStruct;  
   void (__clrcall MyStruct::*F1)() = & MyStruct::f;   // C2843  
   void (__clrcall MyStruct::*F2)() = & ps->f;   // C2843  
   void (__clrcall MyStruct::*F3)();   // C2843  
  
   void (__clrcall *F5)() = MyStruct::sf;   // OK  
   void (__clrcall *F6)() = & ps->sf;   // OK  
  
   int __gc *i = &C::m_i; // C2843  
   C *x = new C();  
   int __gc *i = &x->m_i;  
}  
```