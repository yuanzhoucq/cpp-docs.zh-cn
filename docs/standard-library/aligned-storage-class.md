---
title: "aligned_storage 类 | Microsoft Docs"
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
  - "aligned_storage"
  - "std::tr1::aligned_storage"
  - "std.tr1.aligned_storage"
  - "std.aligned_storage"
  - "std::aligned_storage"
  - "type_traits/std::aligned_storage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aligned_storage 类 [TR1]"
  - "aligned_storage"
ms.assetid: f255e345-1f05-4d07-81e4-017f420839fb
caps.latest.revision: 23
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# aligned_storage 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

生成适当对齐的类型。  
  
## 语法  
  
```  
template<std::size_t Len, std::size_t Align>  
    struct aligned_storage;  
  
template <std::size_t Len, std::size_t Align = alignment_of<max_align_t>::value>  
    using aligned_storage_t = typename aligned_storage<Len, Align>::type;  
```  
  
#### 参数  
 `Len`  
 对象大小。  
  
 `Align`  
 对象对齐方式。  
  
## 备注  
 模板成员 typedef `type` 是使用的对齐方式的 POD 类型的同义词 `Align` 和大小 `Len`。`Align` 必须等于 `alignment_of<T>::value` 某种 `T`, ，或为默认对齐方式。  
  
## 示例  
  
```  
#include <type_traits>   
#include <iostream>   
  
typedef std::aligned_storage<sizeof (int),   
    std::alignment_of<double>::value>::type New_type;   
int main()   
    {   
    std::cout << "alignment_of<int> == "   
        << std::alignment_of<int>::value << std::endl;   
    std::cout << "aligned to double == "   
        << std::alignment_of<New_type>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
alignment_of < 整数 > = = 为双精度对齐的 4 = = 8  
```  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [alignment\_of 类](../standard-library/alignment-of-class.md)