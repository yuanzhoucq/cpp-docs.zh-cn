---
title: "算法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], C++ algorithm conventions
- algorithms [C++], C++
- C++ Standard Library, algorithms
- algorithm template function C++ library conventions
- conventions [C++], C++ algorithm
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 369479614174e1e66d91e39e3decacaf24268a08
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="algorithms"></a>算法
算法是 C++ 标准库的基础部分。 算法不与容器本身一起使用，而与迭代器一起使用。 因此，大多数（如果不是全部）C++ 标准库容器都可以使用相同的算法。 本部分讨论 C++ 标准库算法的约定和术语。  
  
## <a name="remarks"></a>备注  
 算法模板函数的说明使用几个速记短语：  
  
-   短语“in the range [*A*, *B*)”表示从 *A* 开始到 *B*（不包括 B）的零个或多个离散值的序列。仅当可以从 *A 到达 *B* 时，范围有效；*可将 *A* 存储在对象 *N* (*N* = *A*) 中，零次或多次递增该对象 (++*N*)，使该对象在递增有限次数后等于 *B* (N == B*)。*  
  
-   短语“each *N* in the range [*A*, *B*)”表示 *N* 以值 *A* 开始并递增零次或多次，直至等于值 *B*。*N* == *B* 的情况不在范围内。  
  
-   短语“the lowest value of *N* in the range [*A*, *B*) such that *X*”表示确定范围 [*A*, *B*) 中的每个 *N* 是否满足条件 *X*，直到满足条件 *X*。  
  
-   短语“the highest value of *N* in the range [*A*, *B*) such that *X*”表示确定范围 [*A*, *B*) 中的每个 *N* 是否满足 *X*。 每次满足条件 *X*，该函数即在 `K` 中存储 *N* 的一个副本。 如果发生此类存储，则该函数将 *N* 的最终值（等于 *B*）替换为值 `K`。 但是，对于双向或随机访问迭代器，这也可以是意味着 *N* 从范围内的最高值开始在范围内递减，直到满足条件 *X*。  
  
-   表达式如 *X* - *Y*，其中*X* 和 *Y* 可以是随机访问迭代器以外的迭代器，从数学意义上来说是需要的。 如果该函数必须确定此类值，则它不一定会评估 operator**-**。 对于 *X* + *N* 和 *X* - *N* 等表达式也是如此，其中 *N* 是整数类型。  
  
 几种算法使用进行成对比较的谓词（例如 `operator==`）生成 `bool` 结果。 谓词函数 `operator==` 或其任何替代函数不得更改其任一操作数。 每次计算都必须生成相同的 `bool` 结果，且当任一操作数的副本替换了操作数时，也必须生成相同的结果。  
  
 几种算法使用对序列中的元素对执行严格弱排序的谓词。 对于谓词 `pr`(*X*, *Y*)：  
  
-   严格意味着 `pr`(*X*, *X*) 为 false。  
  
-   弱意味着如果 !`pr`(*X*, *Y*) && !`pr`(*Y*, *X*)，则 *X* 和 *Y* 具有等效排序（无需定义 *X* == *Y*）。  
  
-   排序意味着 `pr`(*X*, *Y*) (&& ) `pr`(*Y*, Z) 表示 `pr`(*X*, Z)。  
  
 以上这些算法隐式使用谓词 *X* \< *Y*。通常满足严格弱排序需求的其他谓词有 *X*  >  *Y*、**less**(*X*、*Y*) 和 `greater`(*X*, *Y*)。 但请注意，*X* \<= *Y* 和 *X* >= *Y* 等谓词不满足这一需求。  
  
 如果对于范围 [0, `Last` - `First`) 中的每个 *N* 和范围 (N,`Last` - `First`) 中的每个 *M*，谓词 !(\*(`First` + *M*) < \*(*First* + *N*)) 为 true，则由迭代器在范围 [`First`, `Last`) 内指定的元素序列是按 operator**<** 排序的序列。 （请注意元素以升序进行排序）。谓词函数 **operator<** 或任何其替代函数不得更改其任一操作数。 每次计算都必须生成相同的 `bool` 结果，且当任一操作数的副本替换了操作数时，也必须生成相同的结果。 此外，必须对它比较的操作数进行严格弱排序。  
  
 如果对于范围 [1, `Last` - `First`) 中的每个 *N*，谓词 !(\*`First` < \*(`First` + *N*)) 为 true，则由迭代器在范围 [`First`, `Last`) 内指定的元素序列是按 **operator<** 排序的堆。 （第一个元素最大。）仅对模板函数否则已知其内部结构[make_heap](../standard-library/algorithm-functions.md#make_heap)， [pop_heap](../standard-library/algorithm-functions.md#pop_heap)，和[push_heap](../standard-library/algorithm-functions.md#push_heap)。 就有序序列来说，谓词函数 **operator<**（或其任何替代函数）不得更改任一操作数，且必须对将它比较的操作数进行严格弱排序。 每次计算都必须生成相同的 `bool` 结果，且当任一操作数的副本替换了操作数时，也必须生成相同的结果。  
  
 C++ 标准库算法位于 [\<algorithm>](../standard-library/algorithm.md) 和 [\<numeric>](../standard-library/numeric.md) 标头文件中。  
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

