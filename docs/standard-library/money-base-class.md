---
title: "money_base 类 | Microsoft Docs"
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
  - "locale/std::money_base"
  - "money_base"
  - "std::money_base"
  - "std.money_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "money_base 类"
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# money_base 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

类描述了枚举和一结构模板共有类的所有专用化。[moneypunct](../standard-library/moneypunct-class.md)  
  
## 语法  
  
```  
struct money_base : public locale::facet  
{  
    enum  
    {  
        symbol = '$',  
        sign = '+',  
        space = ' ',  
        value = 'v',  
        none = 'x'  
    };  
    typedef int part;  
    struct pattern  
    {  
        char field[_PATTERN_FIELD_SIZE];  
    };  
    money_base(  
        size_t _Refs = 0  
    );  
    ~money_base();  
};  
```  
  
## 备注  
 枚举在 **part** 数组字段的元素描述可能值结构模式。  **part** 值为：  
  
-   匹配零个或多个空格的**none** 或生成。  
  
-   匹配或生成带有正负号的**sign**。  
  
-   匹配零个或多个空格或**空间** 生成的空间。  
  
-   生成匹配或货币符号的**符号**。  
  
-   匹配或包含一个货币值的**值**。  
  
## 要求  
 **页眉：** \<区域设置\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)