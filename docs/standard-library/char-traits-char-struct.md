---
title: "char_traits&lt;char&gt; 结构 | Microsoft Docs"
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
  - "string/std::char_traits<char>"
  - "std::char_traits<char >"
  - "char_traits<char >"
  - "std.char_traits<char >"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "char_traits<char> 类"
ms.assetid: abd9373a-77db-4031-bf4b-f8ac15087581
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# char_traits&lt;char&gt; 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为模板结构 **char\_traits\<CharType\>** 专用化到 `char`类型元素的结构。  
  
## 语法  
  
```  
template<> struct char_traits<char>;  
```  
  
## 备注  
 专用化允许结构利用操作此类型 `char`对象的库函数。  
  
## 示例  
 对于涉及 `char`类型元素的示例参见 [char\_traits 类](../standard-library/char-traits-struct.md)\> \<**CharType**和 typedef 模板类的成员函数。  
  
## 要求  
 **标头：**\< 字符串\>  
  
 **命名空间:**  std