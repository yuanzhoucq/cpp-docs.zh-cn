---
title: "regex_traits &lt; char &gt; 类 | Microsoft Docs"
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
  - "std::tr1::regex_traits<char>"
  - "regex_traits<char>"
  - "std.tr1.regex_traits<char>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex_traits < char > 类 [TR1]"
ms.assetid: ce95ebcd-3687-4ad5-bf1d-b89fdc633675
caps.latest.revision: 17
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# regex_traits &lt; char &gt; 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用于 char 的 regex\_traits 的专用化。  
  
## 语法  
  
```  
template <>  
    class regex_traits<char>  
```  
  
## 备注  
 此类是模板类的显式专用化 [regex\_traits 类](../standard-library/regex-traits-class.md) 类型元素的 `char` （以便它可以利用库函数时，处理此类型的对象）。  
  
## 要求  
 **标头：**\<regex\>  
  
 **命名空间：**std  
  
## 请参阅  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_traits 类](../standard-library/regex-traits-class.md)