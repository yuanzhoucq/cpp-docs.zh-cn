---
title: 宽字符
ms.date: 11/04/2016
helpviewer_keywords:
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
ms.openlocfilehash: 619adfd398f3955708df3267613de40e71e15fa6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452060"
---
# <a name="wide-characters"></a>宽字符

**ANSI 3.1.3.4** 包含多个字符的整数字符常量的值或包含多个多字节字符的宽字符常量的值

常规字符常量“ab”具有整数值 (int)0x6162。 当存在多个字节时，以前读取的字节将按 CHAR_BIT 的值向左移位，并使用具有低 CHAR_BIT 位的按位“或”运算符比较下一个字节。 多字节字符常量中的字节数不能超过 sizeof(int)（对于 32 位目标代码，为 4）。

如上所述读取多字节字符常量，并使用 `mbtowc` 运行时函数将其转换为宽字符常量。 如果结果不是有效的宽字符常量，则将发出错误。 在任何情况下，`mbtowc` 函数检查的字节数限制为 `MB_CUR_MAX` 的值。

## <a name="see-also"></a>请参阅

[字符](../c-language/characters.md)