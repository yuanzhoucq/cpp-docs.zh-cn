---
title: 生成文件中的长文件名
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, long filenames
- long filenames
ms.assetid: 626d56fc-8879-46ba-9c2d-dd386c78cccc
ms.openlocfilehash: 758f81e2e1b822c00b54cdaedfe996c9c7db2ef2
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342280"
---
# <a name="long-filenames-in-a-makefile"></a>生成文件中的长文件名

将长文件名用双引号引起来，如下所示：

```
all : "VeryLongFileName.exe"
```

## <a name="see-also"></a>请参阅

[生成文件的内容](contents-of-a-makefile.md)
