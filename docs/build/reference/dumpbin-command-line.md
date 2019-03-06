---
title: DUMPBIN 命令行
ms.date: 11/04/2016
f1_keywords:
- dumpbin
helpviewer_keywords:
- DUMPBIN program, command line
ms.assetid: e6ad17d3-965d-41aa-9dfd-75bb073718d4
ms.openlocfilehash: 4a1ce9f3b6ce3db6687820a4244da54efe38b4ab
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423919"
---
# <a name="dumpbin-command-line"></a>DUMPBIN 命令行

若要运行 DUMPBIN，使用以下语法：

```
DUMPBIN [options] files...
```

指定一个或多个二进制文件，以及控制的信息所需的任何选项。 DUMPBIN 显示到标准输出的信息。 可以将其重定向到文件或使用 /OUT 选项指定输出文件名称。

DUMPBIN 时未指定一个选项，可以对文件运行 DUMPBIN，显示 /SUMMARY 输出。

当你键入命令`dumpbin`DUMPBIN 而无需任何其他命令行输入时，显示一条用法语句总结了其自己的选项。

## <a name="see-also"></a>请参阅

[C/C++ 生成工具](../../build/reference/c-cpp-build-tools.md)<br/>
[DUMPBIN 参考](../../build/reference/dumpbin-reference.md)
