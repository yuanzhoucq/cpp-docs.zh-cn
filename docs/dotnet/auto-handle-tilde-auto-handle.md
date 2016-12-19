---
title: "auto_handle::~auto_handle | Microsoft Docs"
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
  - "auto_handle.~auto_handle"
  - "msclr.auto_handle.~auto_handle"
  - "auto_handle::~auto_handle"
  - "~auto_handle"
  - "msclr::auto_handle::~auto_handle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_handle::~auto_handle"
ms.assetid: e83e95a8-015b-4f27-ad63-70efb3690726
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_handle::~auto_handle
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`auto_handle` 析构函数。  
  
## 语法  
  
```  
~auto_handle();  
```  
  
## 备注  
 析构函数或析构拥有的对象。  
  
## 示例  
  
```  
// msl_auto_handle_dtor.cpp  
// compile with: /clr  
#include "msclr\auto_handle.h"  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
public:  
   ClassA() { Console::WriteLine( "ClassA constructor" ); }  
   ~ClassA() { Console::WriteLine( "ClassA destructor" ); }  
};  
  
int main()  
{  
   // create a new scope for a:  
   {  
      auto_handle<ClassA> a = gcnew ClassA;  
   }  
   // a goes out of scope here, invoking its destructor  
   // which in turns destructs the ClassA object.  
  
   Console::WriteLine( "done" );  
}  
```  
  
  **ClassA 构造函数**  
**ClassA 析构函数**  
**done**   
## 要求  
 **头文件** \<msclr \\ auto\_handle.h\>  
  
 **命名空间** msclr  
  
## 请参阅  
 [auto\_handle 成员](../dotnet/auto-handle-members.md)   
 [auto\_handle::release](../dotnet/auto-handle-release.md)   
 [auto\_handle::auto\_handle](../dotnet/auto-handle-auto-handle.md)