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
ms.openlocfilehash: 6532cb56bb70c82525a13ba53efdd6203ebafb12
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205218"
---
# <a name="algorithms"></a>算法

算法是 C++ 标准库的基础部分。 算法不与容器本身一起使用，而与迭代器一起使用。 因此，大多数（如果不是全部）C++ 标准库容器都可以使用相同的算法。 本部分讨论 C++ 标准库算法的约定和术语。

## <a name="remarks"></a>备注

算法模板函数的说明使用几个速记短语：

- 短语 "in \[ *A*， *B*）" 表示零个或多个离散值的序列 *，其*开头为，但不包括*B*。仅当可以从*a*中访问*B*时，范围有效; 你可以在对象*n* （*n*A）*中存储*  =  *A*，将对象递增零次或多次（+ +*N*），并使对象比较等于*B* （*N*  ==  *B*）。

- 短语 "范围 A，B 中的每个*n* \[ *A*" 表示*N*以值*A*开头，并递增零次或多次，直至等于值*B*。 *B**大小写*  ==  *B*不在范围内。

- 短语 " *N* " （范围 a，b）中的 "N" 的最小值， \[ *A*例如*x*"表示*B*为 a，b 中的每个*n*确定条件*x* \[ *A*，直到满足条件*x* 。 *B*

- 短语 " *N* " （范围 a，b）中的最大值， \[ *A* *x*表示*B*为*X* *N* \[ *a*、 *b*范围内的每个 n 确定 x。 每次满足条件*X*时，函数都存储*N* *的一个副本*。 如果发生此类存储，则函数会将*N*的最后一个值（等于*B*）替换为*K*的值。但对于双向或随机访问迭代器，它还可以表示*N*以范围中的最高值开始，并在范围内递减，直到满足条件*X* 。

- 表达式（如*x*  -  *Y*，其中*x*和*Y*可以是随机访问迭代器以外的迭代器）的数学意义。 **-** 如果该函数必须确定此类值，则它不一定计算运算符。 对于*X*  +  *n*和*x*n 等表达式也是如此  -  *N*，其中*N*是整数类型。

多种算法使用执行成对比较的谓词（例如 with `operator==` ）来生成 **`bool`** 结果。 谓词函数 `operator==` 或其任何替代函数不得更改其任一操作数。 它必须在 **`bool`** 每次计算时都生成相同的结果，并且如果为操作数替换任一操作数的副本，则必须生成相同的结果。

几种算法使用对序列中的元素对执行严格弱排序的谓词。 对于谓词*pred*（*X*， *Y*）：

- Strict 表示*pred*（*x*， *x*）为 false。

- 弱表示如果*X* *Y* \! *pred*（*x*， *y*）  && \! *pred*（*y*， *x*），则 x 和 Y 具有等效排序（*X*  ==  无需定义 x*y* ）。

- 排序意味着*pred*（*x*， *y*）  && *pred*（*y*， *z*）表示*pred*（*x*， *z*）。

其中一些算法隐式使用谓词*X* \< *Y*. Other predicates that typically satisfy the strict weak ordering requirement are *X* > *Y*、 `less` （*x*， *y*）和 `greater` （*x*， *y*）。 但请注意， *X* \<= *Y* and *X* > =  *Y*等谓词不满足此要求。

范围第一个、最后一个的迭代器指定的元素序列 \[ *First*是按运算符排序*Last*的序列 **<** （对于范围0、最后一个的范围中的每个*N* \[ *Last*  -  *First*）和范围内的每个*M* （*N*，*最后*  -  *一个*），谓词 \! （ \* （*第一个*  +  *M*） < \* （*第*一个  +  *N*））为 true。 （请注意，元素按升序排序。）谓词函数 `operator<` 或其任何替代函数不得更改其任一操作数。 它必须在 **`bool`** 每次计算时都生成相同的结果，并且如果为操作数替换任一操作数的副本，则必须生成相同的结果。 此外，必须对它比较的操作数进行严格弱排序。

范围内的迭代器指定的元素序列（ \[ `First` `Last` ）是一个按顺序排序的堆 `operator<` （对于范围 1*中的*每个 \[ ，*最后*  -  *一个*），谓词 \! 为 \* _First_  <  \* *First*  +  *N*true。 （第一个元素最大。）另外，它的内部结构仅对[make_heap](algorithm-functions.md#make_heap)、 [pop_heap](algorithm-functions.md#pop_heap)和[push_heap](algorithm-functions.md#push_heap)的模板函数是已知的。 对于有序序列，谓词函数 `operator<` 或它的任何替换都不得更改其任一操作数，并且它必须对它所比较的操作数施加严格的弱排序。 它必须在 **`bool`** 每次计算时都生成相同的结果，并且如果为操作数替换任一操作数的副本，则必须生成相同的结果。

C + + 标准库算法位于 [\<algorithm>](algorithm.md) 和 [\<numeric>](numeric.md) 标头文件中。

## <a name="see-also"></a>另请参阅

[C + + 标准库参考](cpp-standard-library-reference.md)\
[C + + 标准库中的线程安全](thread-safety-in-the-cpp-standard-library.md)
