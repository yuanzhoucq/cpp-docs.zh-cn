---
title: output_iterator_tag 结构 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::output_iterator_tag
dev_langs:
- C++
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6130a6de2504f2a625677ceaac00d23bdbcd9372
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961079"
---
# <a name="outputiteratortag-struct"></a>output_iterator_tag 结构

一个类，提供返回类型的`iterator_category`代表输出迭代器的函数。

## <a name="syntax"></a>语法

output_iterator_tag 结构{};

## <a name="remarks"></a>备注

分类标记类用作算法选择的编译标记。 模板函数需要查找其迭代器参数的最特定的类别，以便可以在编译时使用最高效的算法。 对于每个 `Iterator` 类型的迭代器，`iterator_traits`< `Iterator`> **::iterator_category** 必须定义为最特定的类别标记，用于描述迭代器的行为。

类型是与相同**迭代器**\< **Iter**> **:: iterator_category**时`Iter`描述一个对象来充当输出迭代器。

和其他迭代器标记一样，此标记不在迭代器的 `value_type` 或 `difference_type` 上进行参数化，因为输出迭代器没有 `value_type` 或 `difference_type`。

## <a name="example"></a>示例

请参阅[iterator_traits](../standard-library/iterator-traits-struct.md)或[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)以举例说明如何使用`iterator_tag`s。

## <a name="requirements"></a>要求

**标头：** \<iterator>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
