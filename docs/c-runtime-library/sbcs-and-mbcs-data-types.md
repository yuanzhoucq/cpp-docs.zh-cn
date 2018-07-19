---
title: SBCS 和 MBCS 数据类型 |Microsoft 文档
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- MBCS
- SBCS
dev_langs:
- C++
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccdec81251589ba36209f878f1fa8b727d7d2b98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409272"
---
# <a name="sbcs-and-mbcs-data-types"></a>SBCS 和 MBCS 数据类型

仅处理一个多字节字符或多字节字符的一个字节的任何 Microsoft MBCS 运行库例程需要一个 `unsigned int` 参数（其中 0x00 <= 字符值 <= 0xFFFF，0x00 <= 字节值 <= 0xFF）。 处理字符串上下文中的多字节的字节或字符的 MBCS 例程需要一个用 `unsigned char` 指针表示的多字节字符串。

> [!CAUTION]
> 多字节字符的每个字节可用一个 8 位 char 表示。 但如果类型为 char 的 SBCS 或 MBCS 单字节字符的值大于 0x7F，则该值为负值。 将此类字符直接转换为 int 或 long 时，结果将由编译器进行符号扩展，因此可能产生意外的结果。

因此，最好将多字节字符的一个字节表示为一个 8 位 `unsigned char`。 或者，为避免产生负数结果，可在将 char 类型的单字节字符转换为 int 或 long 之前将其转换为 `unsigned char`。

由于某些 SBCS 字符串处理函数采用（带符号的）char\* 参数，因此定义 _MBCS 时，编译器会发出类型不匹配的警告。 可通过三种方法来避免此警告（按效率高低的顺序列出）：

1. 使用 TCHAR.H 中的类型安全的内联函数。 这是默认行为。

1. 通过在命令行上定义 _MB_MAP_DIRECT，使用 TCHAR.H 中的直接的宏。 如果执行此操作，必须手动匹配类型。 这是最快的方法，但不是类型安全的方法。

1. 使用 TCHAR.H 中类型安全的静态链接的库函数。 为此，在命令行上定义常量 _NO_INLINING。 这是最慢的方法，但是最能确保类型安全。

## <a name="see-also"></a>请参阅

[国际化](../c-runtime-library/internationalization.md)<br/>
[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
