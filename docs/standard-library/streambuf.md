---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: ca5f53d67bb32e59c20d1d440879144f0a617c66
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686027"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

包含 iostreams 标准标头 \<streambuf > 来定义类模板[basic_streambuf](../standard-library/basic-streambuf-class.md)，这是 iostreams 类操作的基本操作。 此标头通常包含在另一 iostream 标头中；很少会直接包含它。

## <a name="syntax"></a>语法

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|使用**char**作为模板参数的 `basic_streambuf` 的专用化。|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|使用**wchar_t**作为模板参数的 `basic_streambuf` 的专用化。|

### <a name="classes"></a>类

|实例|描述|
|-|-|
|[basic_streambuf 类](basic-streambuf-class.md)|类模板描述用于派生流缓冲区的抽象基类，该缓冲区控制元素与特定的流表示形式之间的来回传输。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
