---
title: "regex_traits&lt;wchar_t&gt; 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::regex_traits<wchar_t>"
  - "regex_traits<wchar_t>"
  - "std.tr1.regex_traits<wchar_t>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex_traits<wchar_t> 类 [TR1]"
ms.assetid: 288d6fdb-fb8e-4a4d-904a-53916be7f95b
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# regex_traits&lt;wchar_t&gt; 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用于 wchar\_t 的 regex\_traits 的专用化。  
  
## 语法  
  
```  
template <>  
    class regex_traits<wchar_t>  
```  
  
## 备注  
 此类是类型为 `wchar_t` 的元素的 [regex\_traits 类](../standard-library/regex-traits-class.md) 模板类的显式专用化（以便它可以充分利用操作此类型对象的库函数）。  
  
## 要求  
 **标头：**\<regex\>  
  
 **命名空间：**std  
  
## 请参阅  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_traits 类](../standard-library/regex-traits-class.md)