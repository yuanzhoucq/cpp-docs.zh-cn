---
title: DUMPBIN 命令行
ms.date: 11/04/2016
helpviewer_keywords:
- DUMPBIN program, command line
ms.assetid: e6ad17d3-965d-41aa-9dfd-75bb073718d4
ms.openlocfilehash: 4f663a74fd57f52aa559270d61df4a130cf7e86f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440074"
---
# <a name="dumpbin-command-line"></a>DUMPBIN 命令行

若要运行 DUMPBIN，请使用以下语法：

```
DUMPBIN [options] files...
```

指定一个或多个二进制文件，以及控制信息所需的任何选项。 DUMPBIN 将信息显示到标准输出。 可以将其重定向到文件，也可以使用/OUT 选项指定输出文件的名称。

如果在未指定选项的情况下在文件上运行 DUMPBIN，则 DUMPBIN 将显示/SUMMARY 输出。

如果在不使用任何其他命令行输入的情况下键入命令 `dumpbin`，则 DUMPBIN 将显示汇总其选项的使用情况语句。

## <a name="see-also"></a>另请参阅

[其他 MSVC 生成工具](c-cpp-build-tools.md)<br/>
[DUMPBIN 参考](dumpbin-reference.md)
