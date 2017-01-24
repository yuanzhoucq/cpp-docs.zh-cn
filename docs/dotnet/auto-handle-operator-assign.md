---
title: "auto_handle::operator= | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "auto_handle::operator="
  - "msclr.auto_handle.operator="
  - "msclr::auto_handle::operator="
  - "auto_handle.operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_handle::operator="
ms.assetid: 503ca172-e766-4a78-af98-36fd48c931ee
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_handle::operator=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

赋值运算符。  
  
## 语法  
  
```  
auto_handle<_element_type> % operator=(  
   auto_handle<_element_type> % _right  
);  
template<typename _other_type>  
auto_handle<_element_type> % operator=(  
   auto_handle<_other_type> % _right  
);  
```  
  
#### 参数  
 `_right`  
 将分配为当前 `auto_handle`的 `auto_handle`。  
  
## 返回值  
 当前 `auto_handle`，现在是 `_right`。  
  
## 示例  
  
```  
// msl_auto_handle_op_assign.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
protected:  
   String^ m_s;     
public:  
   ClassA(String^ s) : m_s(s) {  
      Console::WriteLine( "in ClassA constructor: " + m_s );  
   }  
   ~ClassA() {  
      Console::WriteLine( "in ClassA destructor: " + m_s );  
   }  
  
   virtual void PrintHello() {  
      Console::WriteLine( "Hello from {0} A!", m_s );  
   }  
};  
  
ref class ClassB : ClassA {  
public:     
   ClassB( String^ s ) : ClassA( s ) {}  
   virtual void PrintHello() new {  
      Console::WriteLine( "Hello from {0} B!", m_s );  
   }  
};  
  
int main()  
{  
   auto_handle<ClassA> a;  
   auto_handle<ClassA> a2(gcnew ClassA( "first" ) );  
   a = a2; // assign from same type  
   a->PrintHello();  
  
   auto_handle<ClassB> b(gcnew ClassB( "second" ) );     
   b->PrintHello();  
   a = b; // assign from derived type     
   a->PrintHello();  
  
   Console::WriteLine("done");  
}  
```  
  
  **在 ClassA 构造函数：首先**  
**从第一个A开始。**  
**在 ClassA 构造函数：秒**  
**Hello 从第二 B\!**  
**在 ClassA 析构函数：首先**  
**Hello 从第二 A\!**  
**done**  
**在 ClassA 析构函数：秒**   
## 要求  
 **头文件** \<msclr\\auto\_handle.h\>  
  
 **Namespace** msclr  
  
## 请参阅  
 [auto\_handle 成员](../dotnet/auto-handle-members.md)