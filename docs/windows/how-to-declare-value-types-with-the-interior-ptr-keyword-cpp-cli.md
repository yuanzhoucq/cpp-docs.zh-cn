---
title: "如何：用 interior_ptr 关键字声明值类型 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ptr 关键字"
  - "值类型, 声明"
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：用 interior_ptr 关键字声明值类型 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 `interior_ptr` 的值类型。  
  
> [!IMPORTANT]
>  此语言功能支持使用 **\/clr** 编译器选项，但是，不受 **\/ZW** 编译器选项。  
  
## 示例  
  
### 说明  
 下面的 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] 示例演示如何使用值类型的 `interior_ptr`。  
  
### 代码  
  
```  
// interior_ptr_value_types.cpp  
// compile with: /clr  
value struct V {  
   V(int i) : data(i){}  
   int data;  
};  
  
int main() {  
   V v(1);  
   System::Console::WriteLine(v.data);  
  
   // pointing to a value type  
   interior_ptr<V> pv = &v;  
   pv->data = 2;  
  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
  
   // pointing into a value type  
   interior_ptr<int> pi = &v.data;  
   *pi = 3;  
   System::Console::WriteLine(*pi);  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
}  
```  
  
### Output  
  
```  
1  
2  
2  
3  
3  
3  
```  
  
## 示例  
  
### 说明  
 在值类型指针，`this` 的计算结果为 interior\_ptr。  
  
 在值类型 `V`的非静态成员函数体中，`this` 的值是对象地址调用函数类型为 `interior_ptr<V>` 的表达式。  
  
### 代码  
  
```  
// interior_ptr_value_types_this.cpp  
// compile with: /clr /LD  
value struct V {  
   int data;  
   void f() {  
      interior_ptr<V> pv1 = this;  
      // V* pv2 = this;   error  
   }  
};  
```  
  
## 示例  
  
### 说明  
 下面的示例演示了如何使用 address\-of 包含静态成员的运算符。  
  
 静态 Visual C\+\+ 类型成员的地址为本机指针。静态值类型成员的地址是托管指针，因为值类型成员在运行时堆分配，并且可由垃圾回收器移动。  
  
### 代码  
  
```  
// interior_ptr_value_static.cpp  
// compile with: /clr  
using namespace System;  
value struct V { int i; };  
  
ref struct G {  
   static V v = {22};   
   static int i = 23;   
   static String^ pS = "hello";   
};  
  
int main() {  
   interior_ptr<int> p1 = &G::v.i;  
   Console::WriteLine(*p1);  
  
   interior_ptr<int> p2 = &G::i;  
   Console::WriteLine(*p2);  
  
   interior_ptr<String^> p3 = &G::pS;  
   Console::WriteLine(*p3);  
}  
```  
  
### Output  
  
```  
22  
23  
hello  
```  
  
## 请参阅  
 [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)