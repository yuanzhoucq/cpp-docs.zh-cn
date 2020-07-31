---
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: a7df541049aafd191e969eaa392ab3706f171926
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224599"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

定义多个类，这些类支持存储在已分配的对象数组中的序列上的 iostreams 操作 **`char`** 。 这类序列可轻松地转换为 C 字符串或者从 C 字符串进行转换。

## <a name="requirements"></a>要求

**标头：**\<strstream>

**命名空间:** std

## <a name="remarks"></a>备注

类型的对象使用 `strstream` **`char`** *，即 C 字符串。 用于 [\<sstream>](../standard-library/sstream.md) 处理[basic_string](../standard-library/basic-string-class.md)类型的对象。

> [!NOTE]
> \<strstream> 中的类已弃用。 请考虑转而使用 \<sstream> 中的类。

## <a name="members"></a>成员

### <a name="classes"></a>类

|||
|-|-|
|[strstreambuf 类](../standard-library/strstreambuf-class.md)|此类描述一个流缓冲区，该缓冲区控制元素与数组对象中存储的元素序列之间的来回传输 **`char`** 。|
|[istrstream 类](../standard-library/istrstream-class.md)|此类描述了一种对象，该对象可控制从 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区提取元素和编码对象。|
|[ostrstream 类](../standard-library/ostrstream-class.md)|此类描述了一种对象，该对象可控制在 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区中插入元素和编码对象。|
|[strstream 类](../standard-library/strstream-class.md)|此类描述了一种对象，该对象使用 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区控制元素和编码对象的插入和提取。|

### <a name="functions"></a>函数

```cpp
void freeze(bool freezefl = true);
char* str();
int pcount();
```

## <a name="see-also"></a>另请参阅

[\<strstream>](../standard-library/strstream.md)\
[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
