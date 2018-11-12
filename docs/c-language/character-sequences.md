---
title: 字符序列
ms.date: 11/04/2016
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
ms.openlocfilehash: dea24a2ae5887ea8c0111d8251ba4d9d03ccba0f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489656"
---
# <a name="character-sequences"></a>字符序列

**ANSI 3.8.2** 源文件字符序列的映射

预处理器语句使用的字符集和源文件语句相同，只不过转义序列不受支持。

因此，若要指定包含文件的路径，请仅使用一个反斜杠：

```
#include "path1\path2\myfile"
```

在源代码中，需要两个反斜杠：

```
fil = fopen( "path1\\path2\\myfile", "rt" );
```

## <a name="see-also"></a>请参阅

[预处理指令](../c-language/preprocessing-directives.md)