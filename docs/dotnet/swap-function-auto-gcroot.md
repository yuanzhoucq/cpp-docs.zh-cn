---
title: "swap 函数 (auto_gcroot) | Microsoft Docs"
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
  - "msclr::swap"
  - "msclr.swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "swap 函数"
ms.assetid: 2fe8146b-a7f7-445a-9ae9-53b5556be701
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# swap 函数 (auto_gcroot)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将对象`auto_gcroot` 和另一个交换。  
  
## 语法  
  
```  
template<typename _element_type>  
void swap(  
   auto_gcroot<_element_type> & _left,  
   auto_gcroot<_element_type> & _right  
);  
```  
  
#### 参数  
 `_left`  
 一个 `auto_gcroot`。  
  
 `_right`  
 另一个 `auto_gcroot`。  
  
## 示例  
  
```  
// msl_swap_auto_gcroot.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_gcroot<String^> s1 = "string one";  
   auto_gcroot<String^> s2 = "string two";  
  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
   swap( s1, s2 );  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
}  
```  
  
  **s1 \=“strong one"s2 \=“strong two”**  
**s1 \=“strong two"s2 \=“strong one”**   
## 要求  
 **头文件** \<msclr\\auto\_gcroot.h\>  
  
 **Namespace** msclr  
  
## 请参阅  
 [auto\_gcroot](../dotnet/auto-gcroot.md)   
 [auto\_gcroot::swap](../dotnet/auto-gcroot-swap.md)