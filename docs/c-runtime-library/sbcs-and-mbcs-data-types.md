---
title: SBCS 和 MBCS 数据类型
ms.date: 04/11/2018
f1_keywords:
- MBCS
- SBCS
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
ms.openlocfilehash: 72215b7a3fff638daf02f136e3a107ce8a8a00d5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233907"
---
# <a name="sbcs-and-mbcs-data-types"></a>SBCS 和 MBCS 数据类型

仅处理一个多字节字符或多字节字符的一个字节的任何 Microsoft MBCS 运行时库例程需要一个 **`unsigned int`** 参数（其中 0x00 <= 字符值 <= 0xffff，0x00 <= byte 值 <= 0xff）。 处理字符串上下文中的多字节字节或字符的 MBCS 例程需要将多字节字符字符串表示为 **`unsigned char`** 指针。

> [!CAUTION]
> 多字节字符的每个字节都可以用8位表示 **`char`** 。 但是，类型为的 SBCS 或 MBCS 单字节字符的 **`char`** 值大于0x7f，为负数。 将此类字符直接转换为或时 **`int`** **`long`** ，结果将由编译器进行符号扩展，因此可能产生意外结果。

因此，最好将多字节字符的一个字节表示为一个8位 **`unsigned char`** 。 或者，为避免产生负面结果，只需在将类型的单字节字符转换为 **`char`** **`unsigned char`** 或之前将其转换为 **`int`** **`long`** 。

由于部分字符串处理函数采用（带符号的） **`char`** <strong>\*</strong> 参数，因此在定义 **_MBCS**时，将会出现类型不匹配编译器警告。 可通过三种方法来避免此警告（按效率高低的顺序列出）：

1. 使用 TCHAR.H 中的类型安全的内联函数。 此选项为默认行为。

1. 通过在命令行上定义 _MB_MAP_DIRECT，使用 TCHAR.H 中的直接的宏****。 如果执行此操作，必须手动匹配类型。 这是最快的方法，但不是类型安全的方法。

1. 使用 TCHAR.H 中类型安全的静态链接的库函数。 为此，在命令行上定义常量 _NO_INLINING****。 这是最慢的方法，但是最能确保类型安全。

## <a name="see-also"></a>另请参阅

[国际化](../c-runtime-library/internationalization.md)<br/>
[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
