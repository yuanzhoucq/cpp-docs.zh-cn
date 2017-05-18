---
title: "&lt;数字&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::<numeric>
- std.<numeric>
- <numeric>
dev_langs:
- C++
helpviewer_keywords:
- <numeric> header
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 1af103aee129eee8176d6c34754521f7c2381da7
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ltnumericgt"></a>&lt;数字&gt;
定义执行数值处理算法的容器模板函数。  
  
## <a name="syntax"></a>语法  
  
```  
#include <numeric>  
```  
  
## <a name="remarks"></a>备注  
数字算法类似于 [\<algorithm>](algorithm.md) 中的 C++ 标准库算法，并可以应用于多个数据结构。 这包括标准库容器类（例如 [vector](../standard-library/vector-class.md) 和 [list](../standard-library/list-class.md)）、程序定义的数据结构和满足特定算法需求的元素数组。 这些算法通过迭代器间接访问并遍历容器元素来实现此一般性级别。 这些算法处理通常由开始或末尾位置指定的迭代器范围。 引用的范围必须有效，即范围中的所有指针必须可以取消引用，并且在每个范围的序列中，可从第一个位置递增到达最后一个位置。  
  
 这些算法可扩展每个 C++ 标准库容器的运算和成员函数支持的操作，并允许同时与不同类型的容器对象进行交互。  
  
### <a name="functions"></a>函数  
  
|||  
|-|-|  
|[accumulate](../standard-library/numeric-functions.md#accumulate)|通过计算连续的部分和来计算指定范围中所有元素的总和（包括初始值），或计算通过使用指定二元运算而非求和运算获得的连续部分结果的结果总和。|  
|[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)|计算输入范围中每个元素与其前一元素之间的连续差值，并将结果输出到目标范围，或计算将差值运算替换为其他指定二元运算的一般化程序的结果。|  
|[inner_product](../standard-library/numeric-functions.md#inner_product)|计算两个范围的逐元素集乘积的总和并将总和添加到指定初始值，或计算将求和与乘积运算替换为其他指定二元运算的一般化程序的结果。|  
|[iota](../standard-library/numeric-functions.md#iota)|存储一个起始值，从第一个元素开始，在间隔 `value++` 内的每个元素中填充此值的连续递增值 (`[first, last)`)。|  
|[partial_sum](../standard-library/numeric-functions.md#partial_sum)|计算输入范围中从第一个元素到第 *i* 个元素的一系列总和，并在目标范围的第 *i* 个元素中存储每个总和的结果，或计算将求和运算替换为其他指定二元运算的一般化程序的结果。|  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)


