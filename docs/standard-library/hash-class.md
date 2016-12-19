---
title: "hash 类 | Microsoft Docs"
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
  - "std.hash"
  - "xfunctional/std::hash"
  - "hash"
  - "typeindex/std::hash"
  - "std::hash"
  - "std.tr1.hash"
  - "std::tr1::hash"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash 类"
  - "hash 类 [TR1]"
ms.assetid: e1b500c6-a5c8-4f6f-ad33-7ec52eb8e2e4
caps.latest.revision: 22
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# hash 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

计算值的哈希代码。  
  
## 语法  
  
```  
template<class Ty>  
    struct hash  
        : public unary_function<Ty, size_t> {  
    size_t operator()(Ty _Val) const;  
    };  
```  
  
## 备注  
 成员函数定义哈希函数，适合映射值类型到 `Ty` 属性的赋值操作。  成员运算符返回 `_Val`的哈希代码，应用使用类模板 `unordered_map`、`unordered_multimap`、`unordered_set`和 `unordered_multiset`。  `Ty` 可以是任何类型标量、`string`、`wstring`、`error_code`、`error_condition`、`u16string`或 `u32string`。  
  
## 示例  
  
```  
// std_tr1__functional__hash.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
#include <unordered_set>   
  
int main()   
    {   
    std::unordered_set<int, std::hash<int> > c0;   
    c0.insert(3);   
    std::cout << *c0.find(3) << std::endl;   
  
    return (0);   
    }  
  
```  
  
 **3**   
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<unordered\_map\>](../standard-library/unordered-map.md)   
 [unordered\_multimap 类](../standard-library/unordered-multimap-class.md)   
 [unordered\_multiset 类](../standard-library/unordered-multiset-class.md)   
 [\<unordered\_set\>](../standard-library/unordered-set.md)