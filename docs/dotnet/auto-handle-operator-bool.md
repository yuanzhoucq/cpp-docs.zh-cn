---
title: "auto_handle::operator bool | Microsoft Docs"
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
  - "auto_handle.operator bool"
  - "msclr.auto_handle.operator bool"
  - "operator bool"
  - "msclr::auto_handle::operator bool"
  - "auto_handle::operator bool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_handle::operator bool"
ms.assetid: 2e535e99-cf87-4008-b588-02c587d77453
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_handle::operator bool
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在条件表达式中，使用运算符 `auto_handle` 。  
  
## 语法  
  
```  
operator bool();  
```  
  
## 返回值  
 如果指定的对象有效，则为 `true`；否则为 `false`。  
  
## 备注  
 比 `bool` 安全的此运算符实际上转换为 `_detail_class::_safe_bool`，因为它无法转换为整型。  
  
## 示例  
  
```  
// msl_auto_handle_operator_bool.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_handle<String> s1;  
   auto_handle<String> s2 = "hi";  
   if ( s1 ) Console::WriteLine( "s1 is valid" );  
   if ( !s1 ) Console::WriteLine( "s1 is invalid" );  
   if ( s2 ) Console::WriteLine( "s2 is valid" );  
   if ( !s2 ) Console::WriteLine( "s2 is invalid" );  
   s2.reset();  
   if ( s2 ) Console::WriteLine( "s2 is now valid" );  
   if ( !s2 ) Console::WriteLine( "s2 is now invalid" );  
}  
```  
  
  **无效。**  
**s2是有效的**  
**s2 现在无效了**   
## 要求  
 **头文件** \<msclr\\auto\_handle.h\>  
  
 **Namespace** msclr  
  
## 请参阅  
 [auto\_handle 成员](../dotnet/auto-handle-members.md)   
 [auto\_handle::operator\!](../dotnet/auto-handle-operator-logical-not.md)