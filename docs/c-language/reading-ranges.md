---
title: 读取范围
ms.date: 11/04/2016
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
ms.openlocfilehash: 86bb24647084d8bdc452960bab631587c2413276
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343151"
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
