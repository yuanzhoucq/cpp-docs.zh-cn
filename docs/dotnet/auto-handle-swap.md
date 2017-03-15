---
title: "auto_handle::swap | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr::auto_handle::swap"
  - "auto_handle.swap"
  - "auto_handle::swap"
  - "msclr..auto_handle.swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_handle::swap"
ms.assetid: 3ebf82d7-9b69-4a72-a22d-69b4f640f9b0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# auto_handle::swap
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用另一个 `auto_handle`交换对象。  
  
## 语法  
  
```  
void swap(  
   auto_handle<_element_type> % _right  
);  
```  
  
#### 参数  
 `_right`  
 交换的 `auto_handle` 对象。  
  
## 示例  
  
```  
// msl_auto_handle_swap.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_handle<String> s1 = "string one";  
   auto_handle<String> s2 = "string two";  
  
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
 **头文件** \<msclr\\auto\_handle.h\>  
  
 **Namespace** msclr  
  
## 请参阅  
 [auto\_handle 成员](../dotnet/auto-handle-members.md)   
 [swap 函数 \(auto\_handle\)](../dotnet/swap-function-auto-handle.md)