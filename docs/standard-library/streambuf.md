---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: 1121bd4e782fca57588d05fb29b5b9b6cdec18e9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215603"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

包含 iostreams 标准标头 \<streambuf> 以定义[basic_streambuf](../standard-library/basic-streambuf-class.md)的类模板，这是 iostreams 类操作的基本操作。 此标头通常包含在另一 iostream 标头中；很少会直接包含它。

## <a name="syntax"></a>语法

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|`basic_streambuf`使用作为模板参数的的专用化 **`char`** 。|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|`basic_streambuf`使用作为模板参数的的专用化 **`wchar_t`** 。|

### <a name="classes"></a>类

|类|说明|
|-|-|
|[basic_streambuf 类](basic-streambuf-class.md)|类模板描述用于派生流缓冲区的抽象基类，该缓冲区控制元素与特定的流表示形式之间的来回传输。|

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
