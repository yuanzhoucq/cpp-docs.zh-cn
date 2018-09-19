---
title: 字符值的范围 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 15ae9781-ec21-4333-bba8-6d2383bbf7f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b45d828cecb5908742a193c8836bc4b565a6498
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110687"
---
# <a name="range-of-char-values"></a>字符值的范围

**ANSI 3.2.1.1**：“纯”**char** 的值范围与 **signed char** 或 `unsigned char` 的值范围是否相同

所有带符号的字符值的范围都介于 -128 和 127 之间。 所有无符号的字符值的范围介于 0 和 255 之间。

/J 编译器选项将默认值从 **signed** 更改为 `unsigned`。

## <a name="see-also"></a>请参阅

[字符](../c-language/characters.md)