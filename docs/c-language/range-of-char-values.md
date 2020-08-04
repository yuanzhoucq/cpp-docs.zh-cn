---
title: 字符值的范围
ms.date: 11/04/2016
ms.assetid: 15ae9781-ec21-4333-bba8-6d2383bbf7f1
ms.openlocfilehash: 085f7a319cb193f9d9d744d6e896062e550404cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227798"
---
# <a name="range-of-char-values"></a>字符值的范围

ANSI 3.2.1.1“普通”`char` 的值范围是否与 `signed char` 或 `unsigned char` 相同

所有带符号的字符值的范围都介于 -128 和 127 之间。 所有无符号的字符值的范围介于 0 和 255 之间。

[`/J`](../build/reference/j-default-char-type-is-unsigned.md) 编译器选项将 `char` 的默认类型从 `signed char` 更改为 `unsigned char`。

## <a name="see-also"></a>请参阅

[字符](../c-language/characters.md)
