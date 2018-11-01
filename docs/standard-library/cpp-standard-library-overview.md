---
title: C++ 标准库概述
ms.date: 11/04/2016
helpviewer_keywords:
- headers, C++ library
- C++ Standard Library
- libraries, Standard C++
- C++ Standard Library, headers
ms.assetid: 7acb83a4-da73-4ad3-bc30-a71289db7f60
ms.openlocfilehash: 57abafbcbd899d3eca7369205afba4ca262ad2c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444988"
---
# <a name="c-standard-library-overview"></a>C++ 标准库概述

所有 C++ 库实体都在在一个或多个标准标头中声明或定义。 此实现包括两个额外标头\<hash_map > 和\<hash_set >，这不是必需的 c + + 标准。 有关此实现支持的标头的完整列表，请参阅[头文件参考](../standard-library/cpp-standard-library-header-files.md)。

C++ 库的独立式实现仅提供了这些标头的一个子集：

|||
|-|-|
|[\<cstddef>](../standard-library/cstddef.md)|[\<cstdlib>](../standard-library/cstdlib.md)（至少声明函数 `abort`、`atexit` 和 `exit`）|
|[\<exception>](../standard-library/exception.md)|[\<limits>](../standard-library/limits.md)|
|[\<new>](../standard-library/new.md)|[\<cstdarg>](../standard-library/cstdarg.md)|

C++ 库标头有两个更广泛的细分：

- [iostreams](../standard-library/iostreams-conventions.md) 约定。

- [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)约定。

本节包含以下部分：

- [使用 C++ 库标头](../standard-library/using-cpp-library-headers.md)

- [C++ 库约定](../standard-library/cpp-library-conventions.md)

- [iostreams 约定](../standard-library/iostreams-conventions.md)

- [C++ 程序启动和终止](../standard-library/cpp-program-startup-and-termination.md)

- [安全库：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)

- [经检查的迭代器](../standard-library/checked-iterators.md)

- [Debug Iterator Support](../standard-library/debug-iterator-support.md)

- [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)

- [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

- [stdext 命名空间](../standard-library/stdext-namespace.md)

- [正则表达式 (C++)](../standard-library/regular-expressions-cpp.md)

有关 Visual C++ 运行时库的详细信息，请参阅 [CRT 库功能](../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>请参阅

[C++ 标准库](../standard-library/cpp-standard-library-reference.md)<br/>
