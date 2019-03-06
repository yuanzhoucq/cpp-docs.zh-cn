---
title: 生成文件中的长文件名
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, long filenames
- long filenames
ms.assetid: 626d56fc-8879-46ba-9c2d-dd386c78cccc
ms.openlocfilehash: ff9de4bb480e9df3e8492b3a96adef9ee82bb8d4
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416262"
---
# <a name="long-filenames-in-a-makefile"></a>生成文件中的长文件名

将长文件名用双引号引起来，如下所示：

```
all : "VeryLongFileName.exe"
```

## <a name="see-also"></a>请参阅

[生成文件的内容](../build/contents-of-a-makefile.md)
