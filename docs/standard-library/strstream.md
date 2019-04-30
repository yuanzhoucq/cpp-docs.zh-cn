---
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: 72b96c300aba1729823462ce6671e2f9a5285761
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412262"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

定义支持存储在已分配的数组中的序列上的 iostreams 操作的多个类**char**对象。 这类序列可轻松地转换为 C 字符串或者从 C 字符串进行转换。

## <a name="syntax"></a>语法

```cpp
#include <strstream>
```

## <a name="remarks"></a>备注

类型 `strstream` 的对象使用作为 C 字符串的 `char` *。 使用 [\<sstream>](../standard-library/sstream.md)，以使用类型 [basic_string](../standard-library/basic-string-class.md) 的对象。

> [!NOTE]
> 中的类\<strstream > 已弃用。 请考虑使用中的类\<sstream > 改为。

### <a name="classes"></a>类

|类|描述|
|-|-|
|[strstreambuf 类](../standard-library/strstreambuf-class.md)|此类描述了控制元素与序列中存储的元素的传输的流缓冲区**char**数组对象。|
|[istrstream 类](../standard-library/istrstream-class.md)|此类描述了一种对象，该对象可控制从 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区提取元素和编码对象。|
|[ostrstream 类](../standard-library/ostrstream-class.md)|此类描述了一种对象，该对象可控制在 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区中插入元素和编码对象。|
|[strstream 类](../standard-library/strstream-class.md)|此类描述了一种对象，该对象使用 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区控制元素和编码对象的插入和提取。|

## <a name="see-also"></a>请参阅

[\<strstream>](../standard-library/strstream.md)<br/>
[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>
