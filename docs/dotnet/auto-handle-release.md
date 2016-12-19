---
title: "auto_handle::release | Microsoft Docs"
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
  - "msclr::auto_handle::release"
  - "auto_handle.release"
  - "msclr.auto_handle.release"
  - "auto_handle::release"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_handle::release"
ms.assetid: d4848150-859e-4c61-a946-09d24d3d6577
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_handle::release
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

释放 `auto_handle` 从托管对象。  
  
## 语法  
  
```  
_element_type ^ release();  
```  
  
## 返回值  
 释放的对象。  
  
## 示例  
  
```  
// msl_auto_handle_release.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
   String^ m_s;  
public:  
   ClassA( String^ s ) : m_s( s ) {  
      Console::WriteLine( "ClassA constructor: " + m_s );  
   }  
   ~ClassA() {  
      Console::WriteLine( "ClassA destructor: " + m_s );  
   }  
  
   void PrintHello() {  
      Console::WriteLine( "Hello from {0} A!", m_s );     
   }  
};  
  
int main()  
{  
   ClassA^ a;  
  
   // create a new scope:  
   {  
      auto_handle<ClassA> agc1 = gcnew ClassA( "first" );  
      auto_handle<ClassA> agc2 = gcnew ClassA( "second" );  
      a = agc1.release();  
   }  
   // agc1 and agc2 go out of scope here  
  
   a->PrintHello();  
  
   Console::WriteLine( "done" );  
}  
```  
  
  **ClassA 构造函数：首先**  
**ClassA 构造函数：秒**  
**ClassA 析构函数：秒**  
**Hello\!首先从 A**  
**done**   
## 要求  
 **头文件** \<msclr \\ auto\_handle.h\>  
  
 **命名空间** msclr  
  
## 请参阅  
 [auto\_handle 成员](../dotnet/auto-handle-members.md)   
 [auto\_handle::~auto\_handle](../dotnet/auto-handle-tilde-auto-handle.md)   
 [auto\_handle::reset](../dotnet/auto-handle-reset.md)