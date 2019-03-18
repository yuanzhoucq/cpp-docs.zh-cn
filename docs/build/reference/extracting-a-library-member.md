---
title: 提取库成员
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
ms.openlocfilehash: 6c577300f747d6f546b7caa3c66bddd6a516e16b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818058"
---
# <a name="extracting-a-library-member"></a>提取库成员

LIB 可用于创建一个包含一份现有库的成员的对象 (.obj) 文件。 若要提取的成员的副本，请使用以下语法：

```
LIB library /EXTRACT:member /OUT:objectfile
```

此命令将创建一个名为的.obj 文件*objectfile* ，其中包含一份`member`的*库*。 `member`名称是区分大小写。 您可以提取单个命令中的只有一个成员。 /OUT 选项是必需的;没有默认输出名称。 如果文件调用*objectfile*指定的目录中已存在 (或当前目录中，如果使用未不指定任何目录*objectfile*)，提取*objectfile*替换现有文件。

## <a name="see-also"></a>请参阅

[LIB 引用](lib-reference.md)
