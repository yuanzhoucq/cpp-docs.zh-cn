---
title: iterator 结构 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::iterator
dev_langs:
- C++
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a399fa8a9f8fc9a73d75605f31245e42a2154b7c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963623"
---
# <a name="iterator-struct"></a>iterator 结构

空基结构使用，以确保用户定义的迭代器类可正常配合`iterator_trait`s。

## <a name="syntax"></a>语法

```cpp
struct iterator {
   typedef Category iterator_category;
   typedef Type value_type;
   typedef Distance difference_type;
   typedef Distance distance_type;
   typedef Pointer pointer;
   typedef Reference reference;
   };
```

## <a name="remarks"></a>备注

模板结构充当所有迭代器的一个基类型。 它定义成员类型

- `iterator_category`（模板参数 `Category` 的同义词）。

- `value_type`（模板参数 `Type` 的同义词）。

- `difference_type`（模板参数 `Distance` 的同义词）。

- `distance_type`（模板参数 `Distance` 的同义词）。

- `pointer`（模板参数 `Pointer` 的同义词）。

- `reference`（模板参数 `Reference` 的同义词）。

请注意，`value_type`不应为常量类型即使`pointer`指向的对象**const** `Type`且引用指定的对象**const** `Type`。

## <a name="example"></a>示例

有关如何在迭代器基类中声明和使用这些类型的示例，请参阅 [iterator_traits](../standard-library/iterator-traits-struct.md)。

## <a name="requirements"></a>要求

**标头：** \<iterator>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
