---
title: "rank 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::rank"
  - "std.tr1.rank"
  - "rank"
  - "std.rank"
  - "std::rank"
  - "type_traits/std::rank"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rank 类 [TR1]"
  - "rank"
ms.assetid: bc9f1b8f-800f-46ca-b6f4-d8579ed5406a
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# rank 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取数组维度数。  
  
## 语法  
  
```  
template<class Ty>  
    struct rank;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 类型查询会保留数组类型 `Ty` 的维度数值，如果 `Ty` 不是数组类型，则为 0。  
  
## 示例  
  
```  
// std_tr1__type_traits__rank.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "rank<int> == "   
        << std::rank<int>::value << std::endl;   
    std::cout << "rank<int[5]> == "   
        << std::rank<int[5]>::value << std::endl;   
    std::cout << "rank<int[5][10]> == "   
        << std::rank<int[5][10]>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
级别 < 整数 > = = 0 排名 < int [5] > = = 1 排名 < int [5] [10] > = = 2  
```  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [extent 类](../standard-library/extent-class.md)