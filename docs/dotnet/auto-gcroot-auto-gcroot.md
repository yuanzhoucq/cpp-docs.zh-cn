---
title: "auto_gcroot::auto_gcroot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr::auto_gcroot::auto_gcroot"
  - "auto_gcroot::auto_gcroot"
  - "auto_gcroot.auto_gcroot"
  - "msclr.auto_gcroot.auto_gcroot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_gcroot::auto_gcroot"
ms.assetid: 27faa42a-64ea-4d31-836f-073a55145735
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# auto_gcroot::auto_gcroot
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`auto_gcroot` 构造函数。  
  
## 语法  
  
```  
auto_gcroot(  
   _element_type _ptr = nullptr  
);  
auto_gcroot(  
   auto_gcroot<_element_type> & _right  
);  
template<typename _other_type>  
auto_gcroot(  
   auto_gcroot<_other_type> & _right  
);  
```  
  
#### 参数  
 `_ptr`  
 要添加对象的拥有者。  
  
 `_right`  
 现有 `auto_gcroot`。  
  
## 备注  
 当从现有 `auto_gcroot`的 `auto_gcroot` 时，现有 `auto_gcroot` 的所有权转移在对象之前释放其对象添加到新的 `auto_gcroot`。  
  
## 示例  
  
```  
// msl_auto_gcroot_auto_gcroot.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class RefClassA {  
protected:  
   String^ m_s;     
public:  
   RefClassA(String^ s) : m_s(s) {  
      Console::WriteLine( "in RefClassA constructor: " + m_s );  
   }  
   ~RefClassA() {  
      Console::WriteLine( "in RefClassA destructor: " + m_s );  
   }  
  
   virtual void PrintHello() {  
      Console::WriteLine( "Hello from {0} A!", m_s );  
   }  
};  
  
ref class RefClassB : RefClassA {  
public:     
   RefClassB( String^ s ) : RefClassA( s ) {}  
   virtual void PrintHello() new {  
      Console::WriteLine( "Hello from {0} B!", m_s );  
   }  
};  
  
class ClassA { //unmanaged class  
private:     
   auto_gcroot<RefClassA^> m_a;  
  
public:  
   ClassA() : m_a( gcnew RefClassA( "unmanaged" ) ) {}  
   ~ClassA() {} //no need to delete m_a  
  
   void DoSomething() {  
      m_a->PrintHello();  
   }  
};  
  
int main()  
{  
   {  
      ClassA a;  
      a.DoSomething();  
   } // a.m_a is automatically destroyed as a goes out of scope  
  
   {  
      auto_gcroot<RefClassA^> a(gcnew RefClassA( "first" ) );  
      a->PrintHello();  
   }  
  
   {  
      auto_gcroot<RefClassB^> b(gcnew RefClassB( "second" ) );  
      b->PrintHello();  
      auto_gcroot<RefClassA^> a(b); //construct from derived type  
      a->PrintHello();  
      auto_gcroot<RefClassA^> a2(a); //construct from same type  
      a2->PrintHello();  
   }  
  
   Console::WriteLine("done");  
}  
```  
  
  **在 RefClassA 构造函数：非托管**  
**Hello 来自非托管的A。**  
**在 RefClassA 析构函数：非托管**  
**在RefClassA构造函数：首先**  
**从第一个A开始！**  
**在RefClassA析构函数：首先**  
**RefClassA构造函数：第二步**  
**Hello 从第二 B\!**  
**Hello 从第二 A\!**  
**Hello 从第二 A\!**  
**在RefClassA 析构函数：秒**  
**done**   
## 要求  
 **头文件** \<msclr\\auto\_gcroot.h\>  
  
 **Namespace** msclr  
  
## 请参阅  
 [auto\_gcroot Members](../dotnet/auto-gcroot-members.md)   
 [auto\_gcroot::attach](../dotnet/auto-gcroot-attach.md)   
 [auto\_gcroot::operator\=](../dotnet/auto-gcroot-operator-assign.md)   
 [auto\_gcroot::~auto\_gcroot](../dotnet/auto-gcroot-tilde-auto-gcroot.md)