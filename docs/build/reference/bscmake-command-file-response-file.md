---
title: BSCMAKE 命令文件（响应文件）
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
ms.openlocfilehash: beb3d5696957f6b1af8168e3194e3943a1574be8
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820307"
---
# <a name="bscmake-command-file-response-file"></a>BSCMAKE 命令文件（响应文件）

您可以提供部分或全部命令文件中的命令行输入。 指定命令文件使用以下语法：

```
BSCMAKE @filename
```

允许只能有一个命令文件。 您可以指定带有路径*文件名*。 前加上*文件名*使用 at 符号 (**\@**)。 BSCMAKE 不会假设扩展。 您可以指定其他*sbrfiles*后在命令行上*filename*。 命令文件是包含 BSCMAKE 按相同顺序的输入，如您在命令行上指定的文本文件。 使用一个或多个空格、 制表符或换行字符分隔的命令行参数。

以下命令调用 BSCMAKE 使用命令文件：

```
BSCMAKE @prog1.txt
```

下面是示例命令文件：

```
/n /v /o main.bsc /El
/S (
toolbox.h
verdate.h c:\src\inc\screen.h
)
file1.sbr file2.sbr file3.sbr file4.sbr
```

## <a name="see-also"></a>请参阅

[BSCMAKE 参考](bscmake-reference.md)
