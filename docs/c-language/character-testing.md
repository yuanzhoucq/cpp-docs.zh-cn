---
title: 字符测试
ms.date: 11/04/2016
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
ms.openlocfilehash: b02d07ca2796e5088c3021f1ae8795ea92761943
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147186"
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
