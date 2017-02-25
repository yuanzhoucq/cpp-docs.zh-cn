---
title: "bitset 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bitset/std::bitset"
  - "std::bitset"
  - "std.bitset"
  - "bitset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bitset 类"
ms.assetid: 28b86964-87b4-429c-8124-b6c251b6c50b
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# bitset 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

介绍一种类型的对象，该对象存储由固定数量的位构成的序列，这些位提供一种紧凑方式来保留一组项或条件的标志。  bitset 类支持对 bitset 类型的对象执行操作，此类对象包含位集合并提供对每一个位的定时访问。  
  
## 语法  
  
```  
  
     template <size_t   
     N  
     >  
class bitset  
```  
  
#### 参数  
 *N*  
 使用在编译时必须为已知的 **size\_t** 类型的非零整数指定 bitset 对象中的位数。  
  
## 备注  
 与类似的 [vector\<bool\> 类](../standard-library/vector-bool-class.md)不同，bitset 类没有迭代器，并且不是标准模板库容器。  它与 vector\<bool\> 的不同之处还在于它有某个特定大小，该大小在编译时根据声明 **bitset\<N\>** 时由模板参数 **N** 指定的大小确定并固定。  
  
 如果某个位的值为 1，则该位已设置；如果其值为 0，则该位已重置。  翻转或切换某个位就是将其值从 1 更改到 0 或从 0 到 1。  bitset 中的 **N** 个位由从 0 到 **N** \- 1 的整数值索引，其中 0 索引第一个位的位置，**N**\- 1 索引最后一个位的位置。  
  
### 构造函数  
  
|||  
|-|-|  
|[位组](../Topic/bitset::bitset.md)|构造 `bitset<N>` 类的对象并将位初始化为零、某个指定值或从字符串中的字符获取的值。|  
  
### Typedef  
  
|||  
|-|-|  
|[element\_type](../Topic/bitset::element_type.md)|一个类型，它是 `bool` 数据类型的同义词且可用于引用 `bitset` 中的元素位。|  
  
### 成员函数  
  
|||  
|-|-|  
|[所有](../Topic/bitset::all.md)|测试此 `bitset` 中的所有位以确定它们是否都设置为 `true`。|  
|[任何](../Topic/bitset::any.md)|成员函数测试序列中是否有任何位设置为 1。|  
|[count](../Topic/bitset::count.md)|成员函数返回位序列中设置的位数。|  
|[flip](../Topic/bitset::flip.md)|切换 `bitset` 中的所有位的值或切换位于指定位置的单个位。|  
|[无](../Topic/bitset::none.md)|测试 `bitset` 对象中是否不存在任何已设置为 1 的位。|  
|[重置](../Topic/bitset::reset.md)|将 `bitset` 中的所有位重置为 0 或将位于指定位置的位重置为 0。|  
|[set](../Topic/bitset::set.md)|将 `bitset` 中的所有位设置为 1 或将位于指定位置的位设置为 1。|  
|[size](../Topic/bitset::size.md)|返回 `bitset` 对象中的位数。|  
|[测试](../Topic/bitset::test.md)|测试 `bitset` 中指定位置处的位是否设置为 1。|  
|[to\_string](../Topic/bitset::to_string.md)|将 `bitset` 对象转换为字符串表示形式。|  
|[to\_ullong](../Topic/bitset::to_ullong.md)|将 `bitset` 中的位值的总和作为 `unsigned long long` 返回。|  
|[to\_ulong](../Topic/bitset::to_ulong.md)|将 `bitset` 对象转换为 `unsigned long`，如果将后者用于初始化 `bitset`，则会产生包含的位的序列。|  
  
### 成员类  
  
|||  
|-|-|  
|[引用](../Topic/bitset::reference.md)|一个代理类，它提供对 `bitset`（用于将单个位作为 `bitset` 类的 `operator[]` 的帮助程序类进行访问和操作）中包含的位的引用。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\!\=](../Topic/bitset::operator!=.md)|测试目标 `bitset` 是否与指定的 `bitset` 不相等。|  
|[operator&\=](../Topic/bitset::operator&=.md)|使用逻辑 `AND` 操作执行位组的按位组合。|  
|[运算符 \<\<](../Topic/bitset::operator%3C%3C.md)|将 `bitset` 中的位移动到左侧指定数目的位置并将结果返回到新的 `bitset`。|  
|[operator\<\<\=](../Topic/bitset::operator%3C%3C=.md)|将 `bitset` 中的位移动到左侧指定数目的位置并将结果返回到目标 `bitset`。|  
|[operator\=\=](../Topic/bitset::operator==.md)|测试目标 `bitset` 是否与指定的 `bitset` 相等。|  
|[运算符 \>\>](../Topic/bitset::operator%3E%3E.md)|将 `bitset` 中的位移动到右侧指定数目的位置并将结果返回到新 `bitset`。|  
|[operator\>\>\=](../Topic/bitset::operator%3E%3E=.md)|将 `bitset` 中的位移动到右侧指定数目的位置并将结果返回到目标 `bitset`。|  
|[operator&#91;&#93;](../Topic/bitset::operator.md)|如果 `bitset` 可修改，则返回对 `bitset` 中指定位置处的位的引用；否则返回该位置处的位值。|  
|[operator^\=](../Topic/bitset::operator%5E=.md)|使用独占 `OR` 操作执行位组的按位组合。|  
|[operator&#124;\=](../Topic/bitset::operator%7C=.md)|使用非独占 `OR` 操作执行位组的按位组合。|  
|[operator~](../Topic/bitset::operator~.md)|切换目标 `bitset` 中的所有位并返回结果。|  
  
## 要求  
 **标头：**\<bitset\>  
  
 **命名空间:** std