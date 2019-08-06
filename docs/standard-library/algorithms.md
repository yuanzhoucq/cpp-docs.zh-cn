---
title: 算法
ms.date: 10/18/2018
helpviewer_keywords:
- libraries [C++], C++ algorithm conventions
- algorithms [C++], C++
- C++ Standard Library, algorithms
- algorithm template function C++ library conventions
- conventions [C++], C++ algorithm
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
ms.openlocfilehash: d363dc3f06222121ac5efc79b30516ebd55ff539
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456488"
---
# <a name="algorithms"></a>算法

算法是 C++ 标准库的基础部分。 算法不与容器本身一起使用，而与迭代器一起使用。 因此，大多数（如果不是全部）C++ 标准库容器都可以使用相同的算法。 本部分讨论 C++ 标准库算法的约定和术语。

## <a name="remarks"></a>备注

算法模板函数的说明使用几个速记短语：

- \[短语 "in *A*, *B*)" 表示零个或多个离散值的序列, 其开头为 , 但不包括*B*。仅当可以从访问*B*时, 范围有效 *;* 你可以在对象*n* (*n* = *A*)*中存储,* 将对象递增零次或多次 (+ +*N*), 并使对象比较等于*B*递增量 (*N* == *B*) 之后。

- 短语\["范围*A*, *B*中的每个*n* " 表示*N*以值*A*开头, 并递增零次或多次, 直至等于值*B*。*N* == *B* 的情况不在范围内。

- 短语 " *a*, *b*范围\[内*n*的最小值, *x*" 表示为*a*, *b*中\[的每个*n*确定条件*X* , 直到满足条件*X* 。

- 短语 " *N* " ( \[范围*a*, *b*) 中的最大值, *x*表示为*a*、 *b*范围\[内的每个*n*确定*x* 。 每次满足条件*X*时, 函数都存储*N* *的一个副本*。 如果发生此类存储, 则函数会将*N*的最后一个值 (等于*B*) 替换为*K*的值。但是，对于双向或随机访问迭代器，这也可以是意味着 *N* 从范围内的最高值开始在范围内递减，直到满足条件 *X*。

- 表达式如 *X* - *Y*，其中*X* 和 *Y* 可以是随机访问迭代器以外的迭代器，从数学意义上来说是需要的。 如果该函数必须确定此类 **-** 值, 则它不一定计算运算符。 对于 *X* + *N* 和 *X* - *N* 等表达式也是如此，其中 *N* 是整数类型。

几种算法使用执行成对比较的谓词 (例如 with `operator==`) 来产生**布尔**值结果。 谓词函数 `operator==` 或其任何替代函数不得更改其任一操作数。 它必须在每次计算时都生成相同的**bool**结果, 并且如果任一操作数的副本替换为操作数, 则必须生成相同的结果。

几种算法使用对序列中的元素对执行严格弱排序的谓词。 对于谓词*pred*(*X*, *Y*):

- Strict 表示*pred*(*x*, *x*) 为 false。

- 弱表示如果*pred*(*x*, *y*) & \!& \! *pred*(*y*, *x*), 则*x*和*y*具有等效排序 (*x* == *y*不需要定义)。

- 排序意味着*pred*(*x*, *y*) & & *pred*(*y*, *z*) 表示*pred*(*x*, *z*)。

以上这些算法隐式使用谓词 *X* \< *Y*。通常满足严格弱排序需求的其他谓词为*X* > *Y* `less`、(*x*, *y*) `greater`和 (*x*, *Y*)。 但请注意，*X* \<= *Y* 和 *X* >= *Y* 等谓词不满足这一需求。

\[在*第*一个、*最后*一个的范围 **<** 内的迭代器指定的元素序列是, 如果为范围\[0 中的每个*N* , 则为*最后* - 一个排序的序列。) 以及范围 (*N*,*最后* - *一个*) 中的每个*M*的谓词\!(\*(*第一个* + *M*) \*< (*第一个* + *N*)) 为 true。 （请注意元素以升序进行排序）。谓词函数 `operator<` 或其任何替代函数不得更改其任一操作数。 它必须在每次计算时都生成相同的**bool**结果, 并且如果任一操作数的副本替换为操作数, 则必须生成相同的结果。 此外，必须对它比较的操作数进行严格弱排序。

范围\[ `Last` -  \[ `operator<`   内的迭代器指定的元素序列 () 是一个按顺序排序的堆 (对于范围 1, 最后一个中的每个 N)。 `First`谓词\!(\*_first_ *(前*N))为 true。 < \* +  （第一个元素最大。）另外, 它的内部结构仅对模板函数[make_heap](../standard-library/algorithm-functions.md#make_heap)、 [pop_heap](../standard-library/algorithm-functions.md#pop_heap)和[push_heap](../standard-library/algorithm-functions.md#push_heap)是已知的。 对于有序序列, 谓词函数`operator<`或它的任何替换都不得更改其任一操作数, 并且它必须对它所比较的操作数施加严格的弱排序。 它必须在每次计算时都生成相同的**bool**结果, 并且如果任一操作数的副本替换为操作数, 则必须生成相同的结果。

C++ 标准库算法位于 [\<algorithm>](../standard-library/algorithm.md) 和 [\<numeric>](../standard-library/numeric.md) 标头文件中。

## <a name="see-also"></a>请参阅

[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
