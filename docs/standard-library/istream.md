---
title: '&lt;istream&gt;'
ms.date: 11/04/2016
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
ms.openlocfilehash: 0ad27bf849e8d4b9188868b9a29bf423b4cafafa
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458734"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

定义调解 iostreams 提取的模板类 basic_istream，以及调解插入和提取的模板类 basic_iostream。 标头还定义了一个相关的操控程序。 通常会由另一个 iostreams 标头为你包括此头文件；几乎不需要直接包括它。

## <a name="syntax"></a>语法

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|在`basic_iostream` **char**上专用化的类型。|
|[istream](../standard-library/istream-typedefs.md#istream)|在`basic_istream` **char**上专用化的类型。|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|专用于 **wchar** 的类型 `basic_iostream`。|
|[wistream](../standard-library/istream-typedefs.md#wistream)|专用于 **wchar** 的类型 `basic_istream`。|

### <a name="manipulators"></a>操控器

|||
|-|-|
|[ws](../standard-library/istream-functions.md#ws)|跳过流中的空白。|
|[swap](../standard-library/istream-functions.md#istream_swap)|交换两个流对象。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|从流中提取字符和字符串。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|可以完成输入和输出的流类。|
|[basic_istream](../standard-library/basic-istream-class.md)|此模板类描述一个对象, 该对象控制从流缓冲区提取元素和编码对象, 该缓冲区包含`Elem`类型为的元素, 也称为[char_type](../standard-library/basic-ios-class.md#char_type), 其字符特征由类`Tr`确定。称为[traits_type](../standard-library/basic-ios-class.md#traits_type)。|

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
