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
ms.openlocfilehash: e8084fcbbeb2f1526107584058fc227bbd514d39
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582580"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

定义模板类 [basic_ostream](../standard-library/basic-ostream-class.md)，此模板类可调解 iostreams 的插入。 此标头还定义了若干相关的操控程序。 （此标头通常包含在另一个 iostream 标头中。 很少会直接包含它。）

## <a name="syntax"></a>语法

```cpp
#include <ostream>

```

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|创建从类型`basic_ostream`专用于**char**并`char_traits`专用于**char**。|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|创建从类型`basic_ostream`专用于**wchar_t**并`char_traits`专用于**wchar_t**。|

### <a name="manipulators"></a>操控器

|||
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|终止行并刷新缓冲区。|
|[ends](../standard-library/ostream-functions.md#ends)|终止字符串。|
|[flush](../standard-library/ostream-functions.md#flush)|刷新缓冲区。|
|[swap](../standard-library/ostream-functions.md#swap)|将 `basic_ostream` 对象参数左侧的值与 `basic_ostream` 对象参数右侧的值进行交换。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator<<](../standard-library/ostream-operators.md#op_lt_lt)|将各种类型写入流。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|模板类描述控制元素和编码对象插入到流缓存区中的对象。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>
