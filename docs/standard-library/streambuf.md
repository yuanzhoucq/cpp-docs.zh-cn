---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: 15bfa86a3c697442b66a5f77aa6ea7a9aba5643c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521020"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

包含 iostreams 标准标头 \<streambuf > 来定义此模板类 [basic_streambuf](../standard-library/basic-streambuf-class.md)，这是 iostreams 类的基本操作。 此标头通常包含在另一 iostream 标头中；很少会直接包含它。

## <a name="syntax"></a>语法

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|专用化`basic_streambuf`，它使用**char**作为模板参数。|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|专用化`basic_streambuf`，它使用**wchar_t**作为模板参数。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[basic_streambuf 类](basic-streambuf-class.md)|此模板类描述一个用于派生流缓冲区的抽象基类，该缓冲区控制元素与特定的流表示形式的来回传输。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>
