---
title: "Classes value_compare 类 | Microsoft Docs"
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
  - "std::value_compare"
  - "std.value_compare"
  - "value_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_compare 类"
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Classes value_compare 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供可以通过它们比较值的键确定它们在 hash\_map 的相对顺序比较 hash\_map 元素的函数对象。  
  
## 语法  
  
```  
class value_compare  
    : std::public binary_function<value_type, value_type, bool>   
{  
public:  
    bool operator( )(  
        const value_type& _Left,  
        const value_type& _Right ) const  
        {  
            return ( comp( _Left.first, _Right.first ) );   
        }  
protected:  
    value_compare( const key_compare& c ) : comp (c) { }  
    key_compare comp;  
};  
```  
  
## 备注  
 在 hash\_map 包含的全部元素之间的 value\_compare **value\_types** 提供的比较条件从在单个元素的键之间的一种比较会导致辅助由类构造。  成员函数在 value\_compare 运算符提供的函数对象使用对象存储的 `key_compare` 类型 **组件** 比较两元素 SORT 键组件。  
  
 对于 hash\_sets 和 hash\_multisets，是简单容器的键值与值元素相同，value\_compare 与 `key_compare`等效；对于 hash\_maps 和 hash\_multimaps 没有，因为 `pair` 类型元素的值与元素的键的值不相同。  
  
 在Visual C\+\+ .NET 2003中，成员[\<hash\_map\>](../standard-library/hash-map.md) 和 [\<hash\_set\>](../standard-library/hash-set.md) 头文件不再在std命名空间，而是已经进入了stdext命名空间。  有关更多信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
## 示例  
 有关示例的 [hash\_map::value\_comp](../Topic/hash_map::value_comp.md) 参见的示例演示如何声明和使用 value\_compare。  
  
## 要求  
 **标头:** \<hash\_map\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [binary\_function 结构](../standard-library/binary-function-struct.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)