---
title: "is_error_code_enum 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "future/std::is_error_code_enum"
dev_langs: 
  - "C++"
ms.assetid: 84ae4b99-66d2-41ba-9b50-645fcbe14630
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# is_error_code_enum 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示的专用化 [future\_errc](../Topic/future_errc%20Enumeration.md)[error\_code](../standard-library/error-code-class.md)适合存储。  
  
## 语法  
  
```  
template<>  
struct is_error_code_enum<Future_errc> : public true_type;  
```  
  
## 要求  
 **标头:** future  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<future\>](../standard-library/future.md)