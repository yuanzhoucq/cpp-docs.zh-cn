---
title: "auto_gcroot::operator auto_gcroot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "auto_gcroot.operator auto_gcroot"
  - "auto_gcroot::operator auto_gcroot"
  - "msclr.auto_gcroot.operator auto_gcroot"
  - "msclr::auto_gcroot::operator auto_gcroot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_gcroot 运算符"
ms.assetid: 43e3f27a-9f68-444f-9149-a9282a9b935a
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# auto_gcroot::operator auto_gcroot
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 `auto_gcroot` 和兼容类型之间的类型转换操作。  
  
## 语法  
  
```  
template<typename _other_type>  
operator auto_gcroot<_other_type>();  
```  
  
## 返回值  
 当前 `auto_gcroot` 转换为 `auto_gcroot<_other_type>`。  
  
## 示例  
  
```  
// msl_auto_gcroot_op_auto_gcroot.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
protected:     
   String^ m_s;  
public:  
   ClassA( String^ s ) : m_s( s ) {}  
  
   virtual void PrintHello() {  
      Console::WriteLine( "Hello from {0} A!", m_s );  
   }  
};  
  
ref class ClassB : ClassA {  
public:  
   ClassB( String ^ s) : ClassA( s ) {}  
   virtual void PrintHello() new {  
      Console::WriteLine( "Hello from {0} B!", m_s );  
   }  
};  
  
int main() {  
   auto_gcroot<ClassB^> b = gcnew ClassB("first");  
   b->PrintHello();  
   auto_gcroot<ClassA^> a = (auto_gcroot<ClassA^>)b;  
   a->PrintHello();  
}  
```  
  
  **从第一个B开始。**  
**从第一个A开始。**   
## 要求  
 **头文件** \<msclr\\auto\_gcroot.h\>  
  
 **Namespace** msclr  
  
## 请参阅  
 [auto\_gcroot Members](../dotnet/auto-gcroot-members.md)