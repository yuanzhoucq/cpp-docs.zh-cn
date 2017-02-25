---
title: "remove_extent 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::remove_extent"
  - "std.tr1.remove_extent"
  - "remove_extent"
  - "std.remove_extent"
  - "std::remove_extent"
  - "type_traits/std::remove_extent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_extent 类 [TR1]"
  - "remove_extent"
ms.assetid: b9320862-3891-49fc-80bc-571eb2c035cf
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# remove_extent 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从数组类型设置元素类型。  
  
## 语法  
  
```  
template<class T>  
    struct remove_extent;  
  
template<class T>  
using remove_extent_t = typename remove_extent<T>::type;  
```  
  
#### 参数  
 `T`  
 要修改的类型。  
  
## 备注  
 `remove_extent<T>` 的实例保留修改后的类型，当 `T1` 为 `T` 形式时，此类型为 `T1[N]`，否则为 `T`。  
  
## 示例  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "remove_extent_t<int> == "  
        << typeid(std::remove_extent_t<int>).name()  
        << std::endl;T  
    std::cout << "remove_extent_t<int[5]> == "  
        << typeid(std::remove_extent_t<int[5]>).name()  
        << std::endl;T  
    std::cout << "remove_extent_t<int[5][10]> == "  
        << typeid(std::remove_extent_t<int[5][10]>).name()  
        << std::endl;   
    return (0);   
    }  
  
```  
  
  **remove\_extent\_t\<int\> \=\= int**  
**remove\_extent\_t\<int\[5\]\> \=\= int**  
**remove\_extent\_t\<int\[5\]\[10\]\> \=\= int \[10\]**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_all\_extents 类](../standard-library/remove-all-extents-class.md)