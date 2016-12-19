---
title: "char_traits&lt;wchar_t&gt; 结构 | Microsoft Docs"
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
  - "std.char_traits<wchar_t>"
  - "char_traits<wchar_t>"
  - "string/std::char_traits<wchar_t>"
  - "std::char_traits<wchar_t>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "char_traits<wchar_t> 类"
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# char_traits&lt;wchar_t&gt; 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为模板结构 **char\_traits\<CharType\>** 专用化到 `wchar_t`类型元素的类。  
  
## 语法  
  
```  
template<> struct char_traits<wchar_t>;  
```  
  
## 备注  
 专用化允许结构利用操作此类型 `wchar_t`对象的库函数。  
  
## 要求  
 **标头：**\< 字符串\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [char\_traits 结构](../standard-library/char-traits-struct.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)