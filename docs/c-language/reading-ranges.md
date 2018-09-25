---
title: 读取范围 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76530dfdac917dfbde50bc3fb1b17a3c31178729
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030232"
---
# <a name="reading-ranges"></a>读取范围

**ANSI 4.9.6.2**：短划线 (-) 字符的解释，该字符既不是 `fscanf` 函数的 % [ 转换的扫描表中的第一个字符，也不是该表中的最后一个字符

下面的行

```
fscanf( fileptr, "%[A-Z]", strptr);
```

将 A-Z 范围内的任意数目的字符读取到 `strptr` 指向的字符串中。

## <a name="see-also"></a>请参阅

[库函数](../c-language/library-functions.md)