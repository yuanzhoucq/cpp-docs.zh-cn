---
title: 字符测试 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2c558c5d32f75561d5722a656450d5f18f5166a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084934"
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