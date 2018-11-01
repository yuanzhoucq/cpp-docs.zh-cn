---
title: bidirectional_iterator_tag 结构
ms.date: 11/04/2016
f1_keywords:
- xutility/std::bidirectional_iterator_tag
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
ms.openlocfilehash: c8296ddf30c0e2a3d34e69cbf079c0477e0e8b7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661508"
---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag 结构

一个类，提供返回类型的`iterator_category`表示双向迭代器函数。

## <a name="syntax"></a>语法

```cpp
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```

## <a name="remarks"></a>备注

分类标记类用作算法选择的编译标记。 模板函数需要查找其迭代器参数的最具体的分类，以便可以在编译时使用最高效的算法。 对于每个 `Iterator` 类型的迭代器，`iterator_traits`< `Iterator`>:: **iterator_category** 必须定义为最具体的分类标记，用于描述迭代器的行为。

类型是与相同**迭代器**\< **Iter**>:: **iterator_category**时`Iter`描述一个对象来充当双向迭代器。

## <a name="example"></a>示例

有关如何使用 `bidirectional_iterator_tag` 的示例，请参阅 [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)。

## <a name="requirements"></a>要求

**标头：** \<iterator>

**命名空间：** std

## <a name="see-also"></a>请参阅

[forward_iterator_tag 结构](../standard-library/forward-iterator-tag-struct.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
