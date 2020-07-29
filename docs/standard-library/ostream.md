---
title: '&lt;ostream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
ms.openlocfilehash: 37642cbcbe57fba54f071a8fc94af53c97684a36
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228136"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

定义[basic_ostream](../standard-library/basic-ostream-class.md)的类模板，该模板用于调节 iostreams 的插入。 此标头还定义了若干相关的操控程序。 （此标头通常包含在另一个 iostream 标头中。 很少会直接包含它。）

## <a name="syntax"></a>语法

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|基于创建 `basic_ostream` 专用于 **`char`** 并专用于的类型 `char_traits` **`char`** 。|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|基于创建 `basic_ostream` 专用于 **`wchar_t`** 并专用于的类型 `char_traits` **`wchar_t`** 。|

### <a name="manipulators"></a>操控器

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|终止行并刷新缓冲区。|
|[结尾](../standard-library/ostream-functions.md#ends)|终止字符串。|
|[平](../standard-library/ostream-functions.md#flush)|刷新缓冲区。|
|[swap](../standard-library/ostream-functions.md#swap)|将 `basic_ostream` 对象参数左侧的值与 `basic_ostream` 对象参数右侧的值进行交换。|

### <a name="operators"></a>运算符

|操作员|说明|
|-|-|
|[运算符<<](../standard-library/ostream-operators.md#op_lt_lt)|将各种类型写入流。|

### <a name="classes"></a>类

|类|说明|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|类模板描述了控制元素和编码对象插入流缓冲区的对象。|

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
