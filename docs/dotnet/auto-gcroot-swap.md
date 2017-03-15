---
title: "auto_gcroot::swap | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr.auto_gcroot.swap"
  - "msclr::auto_gcroot::swap"
  - "auto_gcroot::swap"
  - "auto_gcroot.swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_gcroot::swap"
ms.assetid: 4915c629-6a53-432c-8155-3a7511dc70cb
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# auto_gcroot::swap
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用另一个 `auto_gcroot`交换对象。  
  
## 语法  
  
```  
void swap(  
   auto_gcroot<_element_type> & _right  
);  
```  
  
#### 参数  
 `_right`  
 交换的 `auto_gcroot` 对象。  
  
## 示例  
  
```  
// msl_auto_gcroot_swap.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_gcroot<String^> s1 = "string one";  
   auto_gcroot<String^> s2 = "string two";  
  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
   s1.swap( s2 );  
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
 [auto\_gcroot Members](../dotnet/auto-gcroot-members.md)   
 [swap 函数 \(auto\_gcroot\)](../dotnet/swap-function-auto-gcroot.md)