---
title: "char_traits&lt;char16_t&gt; 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::char_traits<char16_t>"
  - "std.char_traits<char16_t>"
  - "char_traits<char16_t>"
  - "string/std::char_traits<char16_t>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "char_traits<char16_t> 类"
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# char_traits&lt;char16_t&gt; 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为模板结构 **char\_traits\<CharType\>** 专用化到 `char16_t`类型元素的结构。  
  
## 语法  
  
```  
template<> struct char_traits<char16_t>;  
```  
  
## 备注  
 结构类型专用化允许利用操作 `char16_t`对象的库函数。  
  
## 要求  
 **标头：**\< 字符串\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<string\>](../standard-library/string.md)   
 [char\_traits 结构](../standard-library/char-traits-struct.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)