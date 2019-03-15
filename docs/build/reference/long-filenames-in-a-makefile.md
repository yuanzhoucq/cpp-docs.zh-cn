---
title: 生成文件中的长文件名
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, long filenames
- long filenames
ms.assetid: 626d56fc-8879-46ba-9c2d-dd386c78cccc
ms.openlocfilehash: 758f81e2e1b822c00b54cdaedfe996c9c7db2ef2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825161"
---
# <a name="long-filenames-in-a-makefile"></a>生成文件中的长文件名

将长文件名用双引号引起来，如下所示：

```
all : "VeryLongFileName.exe"
```

## <a name="see-also"></a>请参阅

[生成文件的内容](contents-of-a-makefile.md)
