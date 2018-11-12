---
title: 字符串文本的存储
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
ms.openlocfilehash: b6c266c1381cc7f4e505916a916f5a924a626792
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481219"
---
# <a name="storage-of-string-literals"></a>字符串文本的存储

文本字符串的字符将按顺序存储在连续内存位置。 字符串文本中的转义序列（例如，\\\\ 或 \\"）将作为单个字符进行计数。 null 字符（由 \0 转义序列表示）自动追加到每个字符串并标记该字符串的末尾。 （这会在[转换阶段](../preprocessor/phases-of-translation.md) 7 出现。）请注意，编译器无法在两个不同的地址存储两个相同的字符串。 [/GF](../build/reference/gf-eliminate-duplicate-strings.md) 强制编译器将相同字符串的单个副本置于可执行文件中。

## <a name="remarks"></a>备注

**Microsoft 专用**

字符串具有静态存储持续时间。 有关存储持续时间的信息，请参阅[存储类](../c-language/c-storage-classes.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[C 字符串文本](../c-language/c-string-literals.md)