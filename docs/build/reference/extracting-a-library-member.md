---
title: 提取库成员
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
ms.openlocfilehash: 874866627099eb5aeb318273db26a976e99bac7f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439879"
---
# <a name="extracting-a-library-member"></a>提取库成员

可以使用 LIB 创建对象（.obj）文件，该文件包含现有库的成员的副本。 若要提取成员的副本，请使用以下语法：

```
LIB library /EXTRACT:member /OUT:objectfile
```

此命令创建名为*objectfile*的 .obj 文件，其中包含*库*`member` 的副本。 `member` 名称区分大小写。 只能在单个命令中提取一个成员。 /OUT 选项是必需的;没有默认的输出名称。 如果在指定的目录中已存在名为*objectfile*的文件（或当前目录，则为; 如果未指定带有*objectfile*的目录），则提取的*objectfile*将替换现有文件。

## <a name="see-also"></a>另请参阅

[LIB 引用](lib-reference.md)
