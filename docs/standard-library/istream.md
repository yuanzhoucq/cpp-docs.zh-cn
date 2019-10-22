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
ms.openlocfilehash: 8e9675a673462c8eaab94d29a3ae36a4786737b7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687856"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

定义用于调节 iostreams 提取的类模板 basic_istream，以及用于调节插入和提取的类模板 basic_iostream。 标头还定义了一个相关的操控程序。 通常会由另一个 iostreams 标头为你包括此头文件；几乎不需要直接包括它。

## <a name="syntax"></a>语法

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|在**char**`basic_iostream` 专用化的类型。|
|[istream](../standard-library/istream-typedefs.md#istream)|在**char**`basic_istream` 专用化的类型。|
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

|实例|描述|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|可以完成输入和输出的流类。|
|[basic_istream](../standard-library/basic-istream-class.md)|类模板描述了一个对象，该对象可控制从流缓冲区提取元素和编码对象，其元素类型为 `Elem` （也称为[char_type](../standard-library/basic-ios-class.md#char_type)），其字符特征由类 `Tr` （也称为[traits_type](../standard-library/basic-ios-class.md#traits_type)。|

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
