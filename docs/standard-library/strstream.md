---
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: ecf8499a07f03c00588e7b7fd83b8d41a23e8e7a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459088"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

定义多个类, 这些类支持存储在**char**对象的分配数组中的序列上的 iostreams 操作。 这类序列可轻松地转换为 C 字符串或者从 C 字符串进行转换。

## <a name="requirements"></a>要求

**标头：** \<strstream>

**命名空间：** std

## <a name="remarks"></a>备注

类型 `strstream` 的对象使用作为 C 字符串的 `char` *。 使用 [\<sstream>](../standard-library/sstream.md)，以使用类型 [basic_string](../standard-library/basic-string-class.md) 的对象。

> [!NOTE]
> Strstream > 中\<的类已弃用。 请考虑改用 m 中\<的类 >。

## <a name="members"></a>成员

### <a name="classes"></a>类

|||
|-|-|
|[strstreambuf 类](../standard-library/strstreambuf-class.md)|此类描述一个流缓冲区, 该缓冲区控制元素与**char**数组对象中存储的元素序列之间的来回传输。|
|[istrstream 类](../standard-library/istrstream-class.md)|此类描述了一种对象，该对象可控制从 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区提取元素和编码对象。|
|[ostrstream 类](../standard-library/ostrstream-class.md)|此类描述了一种对象，该对象可控制在 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区中插入元素和编码对象。|
|[strstream 类](../standard-library/strstream-class.md)|此类描述了一种对象，该对象使用 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区控制元素和编码对象的插入和提取。|

### <a name="functions"></a>函数

```cpp
void freeze(bool freezefl = true);
char* str();
int pcount();
```

## <a name="see-also"></a>请参阅

[\<strstream>](../standard-library/strstream.md)\
[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
