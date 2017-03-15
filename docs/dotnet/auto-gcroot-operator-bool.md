---
title: "auto_gcroot::operator bool | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "auto_gcroot.operator bool"
  - "auto_gcroot::operator bool"
  - "msclr.auto_gcroot.operator bool"
  - "msclr::auto_gcroot::operator bool"
  - "operator bool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bool 运算符"
ms.assetid: 87d38498-4221-4de8-8d02-c2dd2e6274ec
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# auto_gcroot::operator bool
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在条件表达式中，使用运算符 `auto_gcroot` 。  
  
## 语法  
  
```  
operator bool() const;  
```  
  
## 返回值  
 如果指定的对象有效，则为 `true`；否则为 `false`。  
  
## 备注  
 比 `bool` 安全的此运算符实际上转换为 `_detail_class::_safe_bool`，因为它无法转换为整型。  
  
## 示例  
  
```  
// msl_auto_gcroot_operator_bool.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_gcroot<String^> s;  
   if ( s ) Console::WriteLine( "s is valid" );  
   if ( !s ) Console::WriteLine( "s is invalid" );  
   s = "something";  
   if ( s ) Console::WriteLine( "now s is valid" );  
   if ( !s ) Console::WriteLine( "now s is invalid" );  
   s.reset();  
   if ( s ) Console::WriteLine( "now s is valid" );  
   if ( !s ) Console::WriteLine( "now s is invalid" );  
}  
```  
  
  **s 是无效的。**  
**当前有效的。**  
**现在s是无效的**   
## 要求  
 **头文件** \<msclr\\auto\_gcroot.h\>  
  
 **Namespace** msclr  
  
## 请参阅  
 [auto\_gcroot Members](../dotnet/auto-gcroot-members.md)   
 [auto\_gcroot::operator\!](../dotnet/auto-gcroot-operator-logical-not.md)