---
title: 将 TCHAR.H 数据类型用于 _MBCS 代码
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
ms.openlocfilehash: dd43c29d77c3351e8f597b474c4756ad3d45ef2b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215356"
---
# <a name="using-tcharh-data-types-with-_mbcs-code"></a>将 TCHAR.H 数据类型用于 _MBCS 代码

定义清单常量后 `_MBCS` ，给定的一般文本例程会映射到以下一种例程：

- 可恰当处理多字节字节、字符和字符串的 SBCS 例程。 在这种情况下，字符串参数的类型应为 **`char*`** 。 例如， `_tprintf` 映射到 `printf` ; 的字符串参数 `printf` 的类型为 **`char*`** 。 如果你将 `_TCHAR` 一般文本数据类型用于字符串类型，则的形参类型与 `printf` 匹配，因为 `_TCHAR*` 映射到 **`char*`** 。

- MBCS 专用例程。 在这种情况下，字符串参数类型应为 `unsigned char*`。 例如，`_tcsrev` 映射到 `_mbsrev`，这应该并且会返回的类型为 `unsigned char*` 的字符串。 如果对 `_TCHAR` 字符串类型使用一般文本数据类型，则可能存在类型冲突，因为 `_TCHAR` 映射到类型 **`char`** 。

以下是防止此类型冲突（以及可能导致的 C 编译器警告或 C++ 编译器错误）的三个解决方案：

- 使用默认行为。 tchar 为运行时库中的例程提供一般文本例程原型，如以下示例中所示。

    ```cpp
    char * _tcsrev(char *);
    ```

   默认情况下，原型 `_tcsrev` `_mbsrev` 通过 Libc 中的 thunk 映射到。 这 `_mbsrev` 会将传入参数和传出返回值的类型从 `_TCHAR*` （即 `char *` ）更改为 `unsigned char *` 。 使用时，此方法可确保类型匹配 `_TCHAR` ，但由于函数调用开销，此方法相对较慢。

- 通过在代码中包含以下预处理器语句来使用函数内联。

    ```cpp
    #define _USE_INLINING
    ```

   此方法导致 tchar 中提供内联函数 thunk，以将一般文本例程直接映射到相应的 MBCS 例程。 下面的代码摘自 tchar，提供了完成此操作的示例。

    ```cpp
    __inline char *_tcsrev(char *_s1)
    {return (char *)_mbsrev((unsigned char *)_s1);}
    ```

   如果可以使用内联，这是最好的解决方案，因为它保证了类型匹配，并且不会产生额外的时间成本。

- 通过在代码中包含以下预处理器语句来使用直接映射。

    ```cpp
    #define _MB_MAP_DIRECT
    ```

   如果不想使用默认行为或无法使用内联，则此方法提供了一种快速替代方法。 这会导致将一般文本例程直接映射到该例程的 MBCS 版本，如 tchar 中的以下示例所示。

    ```cpp
    #define _tcschr _mbschr
    ```

   采用此方法时，必须注意确保对字符串参数和字符串返回值使用适当的数据类型。 可以使用类型强制转换来确保类型匹配正确，也可以使用 `_TXCHAR` 一般文本数据类型。 `_TXCHAR`映射到类型， **`char`** 但映射到 **`unsigned char`** MBCS 代码中的类型。 有关一般文本宏的详细信息，请参阅《*运行时库参考*中的[一般文本映射](../c-runtime-library/generic-text-mappings.md)。

## <a name="see-also"></a>另请参阅

[Tchar 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)
