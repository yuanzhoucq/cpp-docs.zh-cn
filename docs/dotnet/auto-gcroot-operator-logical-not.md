---
title: "auto_gcroot::operator! | Microsoft Docs"
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
  - "msclr.auto_gcroot.operator!"
  - "auto_gcroot.operator!"
  - "msclr::auto_gcroot::operator!"
  - "auto_gcroot::operator!"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_gcroot::operator!"
ms.assetid: f9728be3-2e09-4c01-a594-43e0d59d40d3
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_gcroot::operator!
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

运算符使用 `auto_gcroot` 条件表达式。  
  
## 语法  
  
```  
bool operator!() const;  
```  
  
## 返回值  
 `true`，则包装的对象无效；否则为 `false`。  
  
## 示例  
  
```  
// msl_auto_gcroot_operator_not.cpp  
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
  
  **无效的。**  
**当前有效的。**  
**现在将无效**   
## 要求  
 **头文件** \<msclr \\ auto\_gcroot.h\>  
  
 **命名空间** msclr  
  
## 请参阅  
 [auto\_gcroot Members](../dotnet/auto-gcroot-members.md)   
 [auto\_gcroot::operator bool](../dotnet/auto-gcroot-operator-bool.md)