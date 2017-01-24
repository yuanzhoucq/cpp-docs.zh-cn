---
title: "ctype_base 类 | Microsoft Docs"
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
  - "locale/std::ctype_base"
  - "std.ctype_base"
  - "ctype_base"
  - "std::ctype_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ctype_base 类"
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ctype_base 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

类用作基类。该类模板个 [ctype](../standard-library/ctype-class.md)。  用于定义用于枚举的类型分类或测试字符单个或在整个范围内的 ctype 类的基类。  
  
## 语法  
  
```  
struct ctype_base : public locale::facet  
{  
    enum  
    {  
        alnum, alpha, cntrl, digit, graph,  
        lower, print, punct, space, upper,  
        xdigit  
    };  
    typedef short mask;  
    ctype_base(  
        size_t _Refs = 0  
    );  
    ~ctype_base();  
};  
```  
  
## 备注  
 它定义一枚举掩码。  每一枚举常数分析不同方式排序，如字符定义与标题 \<由声明的类似名称的函数 ctype.h。\>  常数是：  
  
-   **空间** 函数 \( [isspace](../Topic/isspace.md)\)  
  
-   **print** 函数 \( [isprint](../Topic/isprint.md)\)  
  
-   **cntrl** 函数 \( [iscntrl](../Topic/iscntrl.md)\)  
  
-   **upper** 函数 \( [isupper](../Topic/isupper.md)\)  
  
-   **lower** 函数 \( [islower](../Topic/islower.md)\)  
  
-   **digit** 函数 \( [isdigit](../Topic/isdigit.md)\)  
  
-   **punct** 函数 \( [ispunct](../Topic/ispunct.md)\)  
  
-   **xdigit** 函数 \( [isxdigit](../Topic/isxdigit.md)\)  
  
-   **alpha** 函数 \( [isalpha](../Topic/isalpha.md)\)  
  
-   **alnum** 函数 \( [isalnum](../Topic/isalnum.md)\)  
  
-   **graph** 函数 \( [isgraph](../Topic/isgraph.md)\)  
  
 可以按 O 环分析类的组合这些常量。  特别是，始终为 true \(\=\= **alnumalpha** ``&#124; **digit**并 **graphalnum**\(\=\=\)``&#124; **punct**\)。  
  
## 要求  
 **页眉：** \<区域设置\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)