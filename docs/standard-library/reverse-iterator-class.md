---
title: "reverse_iterator 类 | Microsoft Docs"
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
  - "reverse_iterator"
  - "std::reverse_iterator"
  - "std.reverse_iterator"
  - "xutility/std::reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reverse_iterator 类"
ms.assetid: c0b34d04-ae9a-4999-9aff-28b313897ffa
caps.latest.revision: 21
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# reverse_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类是迭代器适配器，描述在行为上与随机访问迭代器或双向迭代器类似（只不过方向相反）的反向迭代器对象。  它允许向后遍历范围。  
  
## 语法  
  
```  
template <class RandomIterator>  
class reverse_iterator  
```  
  
#### 参数  
 RandomIterator  
 一种类型，此类型表示要进行适配化以反向操作的迭代器。  
  
## 备注  
 现有标准模板库容器还定义 `reverse_iterator` 和 `const_reverse_iterator` 类型，并拥有返回反向迭代器的成员函数 `rbegin` 和 `rend`。  这些迭代器具有覆盖语义。  `reverse_iterator` 适配器在提供插入语义时补充此功能，还可与流一起使用。  
  
 需要双向迭代器的 `reverse_iterator` 不能调用 `operator+=`、`operator+`、`operator-=`、`operator-` 或 `operator[]` 中的任何成员函数，这些成员函数只能与随机访问迭代器一起使用。  
  
 如果迭代器范围为 \[`_First`, \_Last\)，其中左侧的方括号指示包含 \_*First*，右侧的括号指示包含到 \_*Left* 的元素，但不包含 \_*Left* 本身。  相同元素包含在反向序列 \[**rev** – `_First`, **rev** – \_*Left*\) 中，这样，如果 \_*Left* 是序列中的超出末尾元素，则反向序列中的第一个元素 **rev** – \_*First* 指向 \*\(\_*Left* – 1 \)。  将所有反向迭代器与其基础迭代器关联的标识是：  
  
 &\*\(**reverse\_iterator** \( *i* \) \) \=\= &\*\( *i* – 1 \)。  
  
 在实际操作中，这意味着在反向序列中，reverse\_iterator 将引用迭代器在原有序列中引用的元素之外（右侧）一个位置的元素。  因此，如果迭代器在序列 \(2, 4, 6, 8\) 中发现元素 6，则 `reverse_iterator` 将在反向序列 \(8, 6, 4, 2\) 中发现元素 4。  
  
### 构造函数  
  
|||  
|-|-|  
|[reverse\_iterator](../Topic/reverse_iterator::reverse_iterator.md)|构造默认 `reverse_iterator` 或从基础迭代器构造 `reverse_iterator`。|  
  
### Typedef  
  
|||  
|-|-|  
|[difference\_type](../Topic/reverse_iterator::difference_type.md)|一种类型，此类型提供引用同一容器中的元素的两个 `reverse_iterator` 之间的差异。|  
|[iterator\_type](../Topic/reverse_iterator::iterator_type.md)|一种类型，此类型为 `reverse_iterator` 提供基础迭代器。|  
|[pointer](../Topic/reverse_iterator::pointer.md)|一种类型，此类型提供指向 `reverse_iterator` 所发现元素的指针。|  
|[reference](../Topic/reverse_iterator::reference.md)|一种类型，此类型提供对 `reverse_iterator` 所发现元素的引用。|  
  
### 成员函数  
  
|||  
|-|-|  
|[base](../Topic/reverse_iterator::base.md)|将基础迭代器从其 `reverse_iterator` 恢复。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\*](../Topic/reverse_iterator::operator*.md)|返回 `reverse_iterator` 发现的元素。|  
|[operator\+](../Topic/reverse_iterator::operator+.md)|将偏移量添加到迭代器，并返回在新偏移位置处发现插入元素的新 `reverse_iterator`。|  
|[operator\+\+](../Topic/reverse_iterator::operator++.md)|将 `reverse_iterator` 递增到下一元素。|  
|[operator\+\=](../Topic/reverse_iterator::operator+=.md)|从 `reverse_iterator` 添加指定偏移量。|  
|[operator\-](../Topic/reverse_iterator::operator-.md)|从 `reverse_iterator` 减去偏移量，并返回在偏移位置处发现元素的 `reverse_iterator`。|  
|[operator\-\-](../Topic/reverse_iterator::operator--.md)|将 `reverse_iterator` 递减到前一元素。|  
|[operator\-\=](../Topic/reverse_iterator::operator-=.md)|从 `reverse_iterator` 减去指定偏移量。|  
|[operator\-\>](../Topic/reverse_iterator::operator-%3E.md)|返回指向 `reverse_iterator` 发现的元素的指针。|  
|[operator&#91;&#93;](../Topic/reverse_iterator::operator.md)|返回对于从 `reverse_iterator` 发现的元素偏移指定个位置的元素的引用。|  
  
## 要求  
 **标头：**\<iterator\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)