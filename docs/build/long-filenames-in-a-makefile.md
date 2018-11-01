---
title: 生成文件中的长文件名
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, long filenames
- long filenames
ms.assetid: 626d56fc-8879-46ba-9c2d-dd386c78cccc
ms.openlocfilehash: 0a0aa950b05d669a560490757ab84a839fc90be9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519374"
---
# <a name="long-filenames-in-a-makefile"></a>生成文件中的长文件名

将长文件名用双引号引起来，如下所示：

```
all : "VeryLongFileName.exe"
```

## <a name="see-also"></a>请参阅

[生成文件的内容](../build/contents-of-a-makefile.md)