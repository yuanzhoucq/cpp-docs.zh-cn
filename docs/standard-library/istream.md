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
ms.openlocfilehash: 37399bb50f195c683b52eea4c8fadf8679d62852
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233088"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

定义 basic_istream 的类模板，该模板用于调节 iostreams 的提取和 basic_iostream 的类模板，该模板可协调插入和提取。 标头还定义了一个相关的操控程序。 通常会由另一个 iostreams 标头为你包括此头文件；几乎不需要直接包括它。

## <a name="syntax"></a>语法

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|专用化的类型 `basic_iostream` **`char`** 。|
|[istream](../standard-library/istream-typedefs.md#istream)|专用化的类型 `basic_istream` **`char`** 。|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|专用于 **wchar** 的类型 `basic_iostream`。|
|[wistream](../standard-library/istream-typedefs.md#wistream)|专用于 **wchar** 的类型 `basic_istream`。|

### <a name="manipulators"></a>操控器

|||
|-|-|
|[ws](../standard-library/istream-functions.md#ws)|跳过流中的空白。|
|[swap](../standard-library/istream-functions.md#istream_swap)|交换两个流对象。|

### <a name="operators"></a>运算符

|操作员|说明|
|-|-|
|[运算符>>](../standard-library/istream-operators.md#op_gt_gt)|从流中提取字符和字符串。|

### <a name="classes"></a>类

|类|说明|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|可以完成输入和输出的流类。|
|[basic_istream](../standard-library/basic-istream-class.md)|类模板描述了一个对象，该对象控制从流缓冲区提取元素和编码对象，该缓冲区包含类型为的元素 `Elem` （也称为[char_type](../standard-library/basic-ios-class.md#char_type)），其字符特征由类 `Tr` （也称为[traits_type](../standard-library/basic-ios-class.md#traits_type)）确定。|

## <a name="see-also"></a>另请参阅

[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
