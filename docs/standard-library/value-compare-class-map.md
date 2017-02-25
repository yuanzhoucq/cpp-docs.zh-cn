---
title: "value_compare 类 (&lt;map&gt;) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::value_compare"
  - "std.value_compare"
  - "map/std::value_compare"
  - "value_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_compare 类"
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# value_compare 类 (&lt;map&gt;)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供可以通过它们比较值的键确定它们在映射的相对顺序比较映射元素的函数对象。  
  
## 语法  
  
```  
class value_compare : public binary_function<value_type, value_type, bool>  
{  
public:  
   bool operator()(const value_type& _Left, const value_type& _Right) const;  
   value_compare(key_compare _Pred) : comp(_Pred);  
   protected:  
      key_compare comp;  
};  
```  
  
## 备注  
 在映射包含的全部元素之间 **value\_types** 的 `value_compare` 提供的比较条件从在单个元素的键之间的一种比较会导致辅助由类构造。  成员函数在 `value_compare` 运算符提供的函数对象使用对象存储的 `key_compare` 类型 **组件** 比较两元素 SORT 键组件。  
  
 对于设置和多集，是简单容器的键值与值元素相同，`value_compare` 等效于 `key_compare`;对于映射和 multimaps 没有，因为 `pair` 类型元素的值与元素的键的值不相同。  
  
## 示例  
 有关示例的 [value\_comp](../Topic/map::value_comp.md) 参见示例演示如何声明和使用 `value_compare`。  
  
## 要求  
 **标头:** \<map\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [binary\_function 结构](../standard-library/binary-function-struct.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)