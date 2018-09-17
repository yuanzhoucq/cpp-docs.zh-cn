---
title: BSCMAKE 命令行 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bda0457eecdf6ef7c846d7c12e24078faa4d0da5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720039"
---
# <a name="bscmake-command-line"></a>BSCMAKE 命令行

若要运行 BSCMAKE，使用以下命令行语法：

```
BSCMAKE [options] sbrfiles
```

选项仅出现在`options`字段在命令行上。

*Sbrfiles*字段指定一个或多个由编译器或组装器创建的.sbr 文件。 用空格或制表符分隔的.sbr 文件的名称。 必须指定扩展;没有默认值。 可以使用文件名，指定的路径，并可以使用操作系统通配符 (\*和？)。

在增量生成，可以指定新的.sbr 文件的内容不属于原始生成。 如果您想保留在浏览信息文件中的所有发布内容，则必须指定所有的.sbr 文件 （包括文件已截断），最初用于创建.bsc 文件。 如果省略的.sbr 文件，则删除该文件的所占的浏览信息文件。

不要指定完全生成的截断的.sbr 文件。 完全编译需要从所有指定的.sbr 文件。 执行完全生成之前，重新编译该项目并创建新的.sbr 文件为每个空文件。

以下命令运行 BSCMAKE 来构建调用 MAIN.bsc 从三个.sbr 文件的文件：

```
BSCMAKE main.sbr file1.sbr file2.sbr
```

有关相关信息，请参阅[BSCMAKE 命令文件](../../build/reference/bscmake-command-file-response-file.md)并[BSCMAKE 选项](../../build/reference/bscmake-options.md)。

## <a name="see-also"></a>请参阅

[BSCMAKE 参考](../../build/reference/bscmake-reference.md)