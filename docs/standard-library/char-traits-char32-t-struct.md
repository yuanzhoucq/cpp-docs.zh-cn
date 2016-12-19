---
title: "char_traits&lt;char32_t&gt; 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "string/std::char_traits<char_32t>"
  - "char_traits<char32_t>"
  - "std.char_traits<char_32t>"
  - "std::char_traits<char_32t>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "char_traits<char32_t> 类"
ms.assetid: c0315466-45d0-4a99-b83e-3b1dbfbfbbc3
caps.latest.revision: 14
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# char_traits&lt;char32_t&gt; 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为模板结构 **char\_traits\<CharType\>** 专用化到 `char32_t`类型元素的结构。  
  
## 语法  
  
```  
template<> struct char_traits<char32_t>;  
```  
  
## 备注  
 专用化允许结构利用操作此类型 `char32_t`对象的库函数。  
  
## 要求  
 **标头：**\< 字符串\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<string\>](../standard-library/string.md)   
 [char\_traits 结构](../standard-library/char-traits-struct.md)