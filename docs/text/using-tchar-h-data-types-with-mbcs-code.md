---
title: 将 TCHAR.H 数据类型用于 _MBCS 代码
ms.date: 11/04/2016
f1_keywords:
- TCHAR
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
ms.openlocfilehash: 0e26aefd8b9099a2ca5e76ce9e2b7d1def2f9854
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410494"
---
# <a name="using-tcharh-data-types-with-mbcs-code"></a>将 TCHAR.H 数据类型用于 _MBCS 代码

当清单常量`_MBCS`是定义，给定的一般文本例程映射到例程的以下类型之一：

- 可恰当处理多字节字节、字符和字符串的 SBCS 例程。 在这种情况下，字符串参数类型应为 `char*`。 例如，`_tprintf` 映射到 `printf`；`printf` 的字符串参数类型为 `char*`。 如果将 `_TCHAR` 一般文本数据类型用于字符串类型，`printf` 的形参和实参类型将匹配，因为 `_TCHAR*` 映射到 `char*`。

- MBCS 专用例程。 在这种情况下，字符串参数类型应为 `unsigned char*`。 例如，`_tcsrev` 映射到 `_mbsrev`，这应该并且会返回的类型为 `unsigned char*` 的字符串。 如果您使用`_TCHAR`一般文本数据类型用于字符串类型，则会潜在的类型冲突，因为`_TCHAR`映射到类型`char`。

以下是防止此类型冲突（以及可能导致的 C 编译器警告或 C++ 编译器错误）的三个解决方案：

- 使用默认行为。 Tchar.h 中的运行时库，如以下示例所示的例程提供一般文本例程原型。

    ```cpp
    char * _tcsrev(char *);
    ```

   默认情况下，对于原型`_tcsrev`映射到`_mbsrev`通过 Libc.lib 中的 thunk。 这会更改的类型`_mbsrev`传入参数和传出返回值从`_TCHAR*`(即`char *`) 到`unsigned char *`。 此方法可确保类型匹配时使用`_TCHAR`，但该过程由于函数调用产生系统开销相对较慢。

- 通过在代码中包含以下预处理器语句来使用函数内联。

    ```cpp
    #define _USE_INLINING
    ```

   此方法会导致内联函数 thunk，tchar.h，一般文本例程直接映射到相应的 MBCS 例程中提供。 以下代码摘自 tchar.h 举例说明如何执行此操作。

    ```cpp
    __inline char *_tcsrev(char *_s1)
    {return (char *)_mbsrev((unsigned char *)_s1);}
    ```

   如果可以使用内联，这是最好的解决方案，因为它保证了类型匹配，并且不会产生额外的时间成本。

- 通过包含在代码中的以下预处理器语句来使用直接的映射。

    ```cpp
    #define _MB_MAP_DIRECT
    ```

   如果不想使用默认行为或无法使用内联，则此方法提供了一种快速替代方法。 它使一般文本例程由宏直接映射到 MBCS 版本的例程，如下面的示例摘自 tchar.h 中所示。

    ```cpp
    #define _tcschr _mbschr
    ```

   采用此方法时，您必须小心以确保使用适当的数据类型的字符串参数和字符串返回值。 可以使用类型强制转换来确保类型匹配正确，也可以使用 `_TXCHAR` 一般文本数据类型。 `_TXCHAR` 映射到类型**char** SBCS 代码映射到类型中**unsigned char** MBCS 代码中。 有关一般文本宏的详细信息，请参阅[一般文本映射](../c-runtime-library/generic-text-mappings.md)中*运行时库参考*。

## <a name="see-also"></a>请参阅

[Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)
