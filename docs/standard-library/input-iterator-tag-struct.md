---
title: input_iterator_tag 结构
ms.date: 11/04/2016
f1_keywords:
- xutility/std::input_iterator_tag
helpviewer_keywords:
- input_iterator_tag class
- input_iterator_tag struct
ms.assetid: ad68a4c6-f315-4ce1-8b74-c1fc71bd1577
ms.openlocfilehash: 5478a8f9fa6013202a1ea8dd838eedb80b9c367e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493920"
---
# <a name="inputiteratortag-struct"></a>input_iterator_tag 结构

一个类，提供返回类型的`iterator_category`代表输入迭代器的函数。

## <a name="syntax"></a>语法

input_iterator_tag 结构{};

## <a name="remarks"></a>备注

分类标记类用作算法选择的编译标记。 模板函数需要查找其迭代器参数的最特定的类别，以便可以在编译时使用最高效的算法。 对于每个 `Iterator` 类型的迭代器，`iterator_traits`< `Iterator`> **::iterator_category** 必须定义为最特定的类别标记，用于描述迭代器的行为。

类型是与相同**迭代器**\< **Iter**> **:: iterator_category**时`Iter`描述一个对象来充当输入迭代器。

## <a name="example"></a>示例

请参阅[iterator_traits](../standard-library/iterator-traits-struct.md)或[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)以举例说明如何使用`iterator_tag`s。

## <a name="requirements"></a>要求

**标头：** \<iterator>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
