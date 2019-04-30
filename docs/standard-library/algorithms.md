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
ms.openlocfilehash: a0a1165d731e44568d530e3ed919d73e2a3e8e5e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411118"
---
# <a name="algorithms"></a>算法

算法是 C++ 标准库的基础部分。 算法不与容器本身一起使用，而与迭代器一起使用。 因此，大多数（如果不是全部）C++ 标准库容器都可以使用相同的算法。 本部分讨论 C++ 标准库算法的约定和术语。

## <a name="remarks"></a>备注

算法模板函数的说明使用几个速记短语：

- 短语"范围内\[ *A*， *B*)"表示从零个或多个离散值的序列*一个*但不是包括*B*.有效范围是仅当*B*可从*A;* 可以存储*一个*对象中*N* (*N*  = *A*)，递增零次或多次的对象 (+ +*N*)，并使该对象的比较结果相等*B*后的有限数量的增量 (*N*  ==  *B*)。

- 短语"每个*N*范围内\[*一个*， *B*)"意味着*N*的值开始，并递增零次或多次直至等于值*B*。*N* == *B* 的情况不在范围内。

- 短语"下限*N*范围内\[*一个*， *B*)，以便*X*"意味着条件*X*确定每个*N*范围内\[*一个*， *B*) 直到条件*X*满足。

- 短语"最高的值*N*范围内\[*一个*， *B*)，以便*X*意味着*X*确定每个*N*范围内\[*一个*， *B*)。 该函数将存储在*K*一份*N*每次条件*X*满足。 如果发生此类存储，该函数将替换的最终值*N*，哪个 equals *B*，值为*K*。但是，对于双向或随机访问迭代器，这也可以是意味着 *N* 从范围内的最高值开始在范围内递减，直到满足条件 *X*。

- 表达式如 *X* - *Y*，其中*X* 和 *Y* 可以是随机访问迭代器以外的迭代器，从数学意义上来说是需要的。 该函数不一定会评估运算符**-** 如果它必须确定此类值。 对于 *X* + *N* 和 *X* - *N* 等表达式也是如此，其中 *N* 是整数类型。

几种算法使用的一个谓词，如执行成对比较`operator==`，以产生**bool**结果。 谓词函数 `operator==` 或其任何替代函数不得更改其任一操作数。 它必须生成相同**bool**导致每次计算，并且它必须生成相同的结果，如果其中一个操作数的副本替换为操作数。

几种算法使用对序列中的元素对执行严格弱排序的谓词。 对于谓词*pred*(*X*， *Y*):

- 严格意味着*pred*(*X*， *X*) 为 false。

- 弱意味着*X*并*Y*具有等效排序 if \! *pred*(*X*， *Y*)& & \! *pred*(*Y*， *X*) (*X* == *Y*不需要进行定义)。

- 排序意味着*pred*(*X*， *Y*) & & *pred*(*Y*， *Z*)暗指*pred*(*X*， *Z*)。

以上这些算法隐式使用谓词 *X* \< *Y*。通常满足严格弱排序需求的其他谓词有*X* > *Y*， `less`(*X*， *Y*)，并`greater`(*X*， *Y*)。 但请注意，*X* \<= *Y* 和 *X* >= *Y* 等谓词不满足这一需求。

指定由迭代器在范围内的元素序列\[*第一个*，*上次*) 是一个排序运算符的序列**<** 当对于每个*N*范围内\[0，*上次* - *第一个*) 以及每个*M*范围内 (*N*，*上次* - *第一个*) 谓词\!(\*(*第一个* +  *M*) < \*(*第一个* + *N*)) 为 true。 （请注意元素以升序进行排序）。谓词函数 `operator<` 或其任何替代函数不得更改其任一操作数。 它必须生成相同**bool**导致每次计算，并且它必须生成相同的结果，如果其中一个操作数的副本替换为操作数。 此外，必须对它比较的操作数进行严格弱排序。

指定由迭代器在范围内的元素序列\[ `First`， `Last`) 由排序的堆`operator<`if、 为每个*N*范围内\[1，*上次* - *第一个*) 谓词\!(\*_第一个_ < \*(*第一个* + *N*)) 为 true。 （第一个元素最大。）其内部结构仅对模板函数已知[make_heap](../standard-library/algorithm-functions.md#make_heap)， [pop_heap](../standard-library/algorithm-functions.md#pop_heap)，并[push_heap](../standard-library/algorithm-functions.md#push_heap)。 作为有序序列，谓词函数`operator<`，或任何其替代，不得更改任一操作数，且必须对进行严格弱排序它比较的操作数。 它必须生成相同**bool**导致每次计算，并且它必须生成相同的结果，如果其中一个操作数的副本替换为操作数。

C++ 标准库算法位于 [\<algorithm>](../standard-library/algorithm.md) 和 [\<numeric>](../standard-library/numeric.md) 标头文件中。

## <a name="see-also"></a>请参阅

[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
