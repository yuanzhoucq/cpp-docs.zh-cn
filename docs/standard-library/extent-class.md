---
title: "extent 类 | Microsoft Docs"
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
  - "std.tr1.extent"
  - "extent"
  - "std::tr1::extent"
  - "std.extent"
  - "std::extent"
  - "type_traits/std::extent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "extent 类 [TR1]"
  - "extent"
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# extent 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取数组维度。  
  
## 语法  
  
```  
template<class Ty, unsigned I = 0>  
    struct extent;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
 `I`  
 绑定到查询的数组。  
  
## 备注  
 如果 `Ty` 是至少具有 `I` 维度的数组类型，则类型查询保留在由 `I` 指定的维度中的元素数。  如果 `Ty` 不是数组类型或它的级别小于 `I`，或者如果 `I` 为零且 `Ty` 属于类型“`U` 的未知绑定的数组”，则类型查询保留值 0。  
  
## 示例  
  
```  
// std_tr1__type_traits__extent.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "extent 0 == "   
        << std::extent<int[5][10]>::value << std::endl;   
    std::cout << "extent 1 == "   
        << std::extent<int[5][10], 1>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **extent 0 \=\= 5**  
**extent 1 \=\= 10**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_all\_extents 类](../standard-library/remove-all-extents-class.md)   
 [remove\_extent 类](../standard-library/remove-extent-class.md)