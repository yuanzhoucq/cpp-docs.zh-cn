---
title: 字符测试
ms.date: 11/04/2016
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
ms.openlocfilehash: 31a90f28d710ffc1b58f9c6b3fcfd01fd8d2d00c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523196"
---
# <a name="character-testing"></a>字符测试

**ANSI 4.3.1**：由 `isalnum`、`isalpha`、`iscntrl`、`islower`、`isprint` 和 `isupper` 函数测试的字符集

以下列表描述了由 Microsoft C 编译器实现的这些函数。

|函数|测试|
|--------------|---------------|
|`isalnum`|字符 0 - 9、A-Z、a–z ASCII 48-57、65-90、97-122|
|`isalpha`|字符 A-Z、a–z ASCII 65-90、97-122|
|`iscntrl`|ASCII 0 -31、127|
|`islower`|字符 a-z ASCII 97-122|
|`isprint`|字符 A–Z、a–z、0 - 9、标点、空格 ASCII 32–126|
|`isupper`|字符 A-Z ASCII 65-90|

## <a name="see-also"></a>请参阅

[库函数](../c-language/library-functions.md)