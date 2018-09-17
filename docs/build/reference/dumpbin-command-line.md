---
title: DUMPBIN 命令行 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- dumpbin
dev_langs:
- C++
helpviewer_keywords:
- DUMPBIN program, command line
ms.assetid: e6ad17d3-965d-41aa-9dfd-75bb073718d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9028cebd7c75bb37bbfa958186ebb2e5d206094
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724757"
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