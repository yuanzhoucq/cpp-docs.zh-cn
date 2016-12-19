---
title: "&lt; &gt; iomanip | Microsoft Docs"
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
  - "iomanip/std::<iomanip>"
  - "std::<iomanip>"
  - "<iomanip>"
  - "std.<iomanip>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iomanip 标头"
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; &gt; iomanip
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含 `iostreams` 标准标头 `<iomanip>` 以定义几个各自采用单个参数的操控器。  
  
## 语法  
  
```  
  
#include <iomanip>  
  
```  
  
## 备注  
 其中每个操控器都返回重载 `basic_istream`\<**Elem**, **Tr**\>`::`[operator\>\>](../Topic/operator%3E%3E%20\(%3Cistream%3E\).md) 和 `basic_ostream`\<**Elem**, **Tr**\>`::`[operator\<\<](../Topic/operator%3C%3C%20\(%3Costream%3E\).md) 的未指定类型（名为 **T1** 到 **T10**）。  
  
### 操控器  
  
|||  
|-|-|  
|[get\_money](../Topic/%3Ciomanip%3E%20get_money.md)|获取货币金额（可选择采用国际格式）。|  
|[get\_time](../Topic/%3Ciomanip%3E%20get_time.md)|使用指定格式以某种时间结构获取时间。|  
|[put\_money](../Topic/%3Ciomanip%3E%20put_money.md)|提供货币金额（可选择采用国际格式）。|  
|[put\_time](../Topic/%3Ciomanip%3E%20put_time.md)|采用要使用的时间结构和格式字符串提供时间。|  
|[带引号](../Topic/quoted.md)|使用插入和提取运算符实现字符串的方便往返。|  
|[resetiosflags](../Topic/resetiosflags.md)|清除指定标志。|  
|[setbase](../Topic/setbase.md)|为整数设置基数。|  
|[setfill](../Topic/setfill.md)|设置用于在右对齐显示中填充空格的字符。|  
|[setiosflags](../Topic/setiosflags.md)|设置指定标志。|  
|[setprecision](../Topic/setprecision.md)|为浮点值设置精度。|  
|[setw](../Topic/setw.md)|指定显示字段的宽度。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)