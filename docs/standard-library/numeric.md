---
title: "&lt; 数字 &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::<numeric>"
  - "std.<numeric>"
  - "<numeric>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "< 数字 > 标头"
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# &lt; 数字 &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义执行数值处理算法的容器模板函数。  
  
## <a name="syntax"></a>语法  
  
```  
#include <numeric>  
```  
  
## <a name="remarks"></a>备注  
 这些算法类似于标准模板库 (STL) 算法，但属于 C++ 标准库。 但是，这些算法与 STL 兼容，并与 STL 算法类似，可在多种数据结构上运行。 这包括 STL 容器类 — 例如， [向量](../standard-library/vector-class.md) 和 [列表](../standard-library/list-class.md), ，和程序定义的数据结构和满足特定算法要求的元素的数组。 这些算法通过迭代器间接访问并遍历容器元素来实现此一般性级别。 这些算法处理通常由开始或末尾位置指定的迭代器范围。 引用的范围必须有效，即范围中的所有指针必须可以取消引用，并且在每个范围的序列中，可从第一个位置递增到达最后一个位置。  
  
 这些算法可扩展每个 STL 容器的运算和成员函数支持的操作，并允许同时与不同类型的容器对象进行交互。  
  
### <a name="functions"></a>函数  
  
|||  
|-|-|  
|[累计](../Topic/%3Cnumeric%3E%20functions.md#accumulate)|通过计算连续的部分和来计算指定范围中所有元素的总和（包括初始值），或计算通过使用指定二元运算而非求和运算获得的连续部分结果的结果总和。|  
|[adjacent_difference](../Topic/%3Cnumeric%3E%20functions.md#adjacent_difference)|计算输入范围中每个元素与其前一元素之间的连续差值，并将结果输出到目标范围，或计算将差值运算替换为其他指定二元运算的一般化程序的结果。|  
|[inner_product](../Topic/%3Cnumeric%3E%20functions.md#inner_product)|计算两个范围的逐元素集乘积的总和并将总和添加到指定初始值，或计算将求和与乘积运算替换为其他指定二元运算的一般化程序的结果。|  
|[iota](../Topic/%3Cnumeric%3E%20functions.md#iota)|存储一个起始值，从第一个元素开始，在间隔 `value++` 内的每个元素中填充此值的连续递增值 (`[first, last)`)。|  
|[partial_sum](../Topic/%3Cnumeric%3E%20functions.md#partial_sum)|计算一系列从第一个元素到输入范围中的总和 *我*th 元素，并将存储在每个总和的结果 *我*th 元素的目标范围，或计算指定二元运算其中由另一个替换求和运算的一般化程序的结果。|  
  
## <a name="see-also"></a>请参阅  
 [标头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)

