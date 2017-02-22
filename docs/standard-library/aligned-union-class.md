---
title: "aligned_union 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "aligned_union"
  - "std.aligned_union"
  - "std::aligned_union"
  - "type_traits/std::aligned_union"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aligned_union"
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# aligned_union 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供用于存储联合类型和所需的大小的 POD 类型足够大，并适当对齐。  
  
## 语法  
  
```  
template <std::size_t Len, class... Types>  
    struct aligned_union;  
  
template <std::size_t Len, class... Types>  
    using aligned_union_t = typename aligned_union<Len, Types...>::type;  
```  
  
#### 参数  
 `Len`  
 联合中的最大类型的对齐值。  
  
 `Types`  
 基础联合中的不同类型。  
  
## 备注  
 使用此模板类来获取的对齐方式和未初始化的存储中存储一个联合所需的大小。 成员 typedef `type` 名称 POD 键入合适的存储中列出的任何类型的 `Types`; 最小大小是 `Len`。 静态成员 `alignment_value` 类型的 `std::size_t` 包含中列出的所有类型的所需的最严格的对齐方式 `Types`。  
  
## 示例  
 下面的示例演示如何使用 `aligned_union` 无法分配对齐的堆栈缓冲区放置联合。  
  
```  
// std__type_traits__aligned_union.cpp  
#include <iostream>  
#include <type_traits>  
  
union U_type  
{  
    int i;  
    float f;  
    double d;  
    U_type(float e) : f(e) {}  
};  
  
typedef std::aligned_union<16, int, float, double>::type aligned_U_type;  
  
int main()  
{  
    // allocate memory for a U_type aligned on a 16-byte boundary  
    aligned_U_type au;  
    // do placement new in the aligned memory on the stack  
    U_type* u = new (&au) U_type(1.0f);  
    if (nullptr != u)  
    {  
        std::cout << "value of u->i is " << u->i << std::endl;  
        // must clean up placement objects manually!  
        u->~U_type();  
    }  
}  
```  
  
```Output  
您的值-> i 是 1065353216  
```  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [alignment\_of 类](../standard-library/alignment-of-class.md)