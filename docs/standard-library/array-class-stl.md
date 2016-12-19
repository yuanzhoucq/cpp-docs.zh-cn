---
title: "array 类 (STL) | Microsoft Docs"
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
  - "array/std::tr1::array"
  - "std.tr1.array"
  - "array"
  - "std::tr1::array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "array 类 [TR1]"
ms.assetid: fdfd43a5-b2b5-4b9e-991f-93bf10fb4293
caps.latest.revision: 22
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# array 类 (STL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述了一个对象，此对象控制类型 `Ty` 的元素的长度序列 `N`。  此序列存储为 `Ty` 的数组，包含在 `array<Ty, N>` 对象中。  
  
## 语法  
  
```  
template<class Ty, std::size_t N>  
    class array;  
```  
  
#### 参数  
  
|||  
|-|-|  
|参数|描述|  
|`Ty`|元素的类型。|  
|`N`|元素数量。|  
  
## 成员  
  
|||  
|-|-|  
|类型定义|说明|  
|[array::const\_iterator](../Topic/array::const_iterator.md)|受控序列的常量迭代器的类型。|  
|[array::const\_pointer](../Topic/array::const_pointer.md)|元素的常量指针的类型。|  
|[array::const\_reference](../Topic/array::const_reference.md)|元素的常量引用的类型。|  
|[array::const\_reverse\_iterator](../Topic/array::const_reverse_iterator.md)|受控序列的常量反向迭代器的类型。|  
|[array::difference\_type](../Topic/array::difference_type.md)|两个元素间的带符号距离的类型。|  
|[array::iterator](../Topic/array::iterator.md)|受控序列的迭代器的类型。|  
|[array::pointer](../Topic/array::pointer.md)|元素的指针的类型。|  
|[array::reference](../Topic/array::reference.md)|元素的引用的类型。|  
|[array::reverse\_iterator](../Topic/array::reverse_iterator.md)|受控序列的反向迭代器的类型。|  
|[array::size\_type](../Topic/array::size_type.md)|两个元素间的无符号距离的类型。|  
|[array::value\_type](../Topic/array::value_type.md)|元素的类型。|  
  
|||  
|-|-|  
|成员函数|说明|  
|[array::array](../Topic/array::array.md)|构造一个数组对象。|  
|[array::assign](../Topic/array::assign.md)|替换所有元素。|  
|[array::at](../Topic/array::at.md)|访问指定位置处的元素。|  
|[array::back](../Topic/array::back.md)|访问最后一个元素。|  
|[array::begin](../Topic/array::begin.md)|指定受控序列的开头。|  
|[array::cbegin](../Topic/array::cbegin.md)|返回一个随机访问常量迭代器，它指向数组中的第一个元素。|  
|[array::cend](../Topic/array::cend.md)|返回一个随机访问常量迭代器，它指向刚超过数组末尾的位置。|  
|[array::crbegin](../Topic/array::crbegin.md)|返回一个指向反向数据中第一个元素的常量迭代器。|  
|[array::crend](../Topic/array::crend.md)|返回一个指向反向数组末尾的常量迭代器。|  
|[array::data](../Topic/array::data.md)|获取第一个元素的地址。|  
|[array::empty](../Topic/array::empty.md)|测试元素是否存在。|  
|[array::end](../Topic/array::end.md)|指定受控序列的末尾。|  
|[array::fill](../Topic/array::fill.md)|将所有元素替换为指定值。|  
|[array::front](../Topic/array::front.md)|访问第一个元素。|  
|[array::max\_size](../Topic/array::max_size.md)|对元素数进行计数。|  
|[array::rbegin](../Topic/array::rbegin.md)|指定反向受控序列的开头。|  
|[array::rend](../Topic/array::rend.md)|指定反向受控序列的末尾。|  
|[array::size](../Topic/array::size.md)|对元素数进行计数。|  
|[array::swap](../Topic/array::swap.md)|交换两个容器的内容。|  
  
|||  
|-|-|  
|运算符|说明|  
|[array::operator\=](../Topic/array::operator=.md)|替换受控序列。|  
|[array::operator](../Topic/array::operator.md)|访问指定位置处的元素。|  
  
## 备注  
 此类型具有默认的构造函数 `array()` 和默认的赋值运算符 `operator=`，并且满足 `aggregate` 的要求。  因此，可使用聚合初始化表达式来初始化类型 `array<Ty, N>` 的对象。  例如，  
  
```  
array<int, 4> ai = { 1, 2, 3 };  
```  
  
 创建包含四个整数值的对象 `ai`，分别将前三个元素初始化为值 1、2 和 3，并将第四个元素初始化为 0。  
  
## 要求  
 **标头：**\<array\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<array\>](../standard-library/array.md)