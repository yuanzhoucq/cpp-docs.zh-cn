---
title: BSCMAKE 命令行
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
ms.openlocfilehash: 61035ce0f211e6a474bb83fc7de7d95b4a29cf3d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272905"
---
# <a name="bscmake-command-line"></a>BSCMAKE 命令行

> [!WARNING]
> 虽然安装 Visual Studio 时仍会安装 BSCMAKE，但 IDE 将不再使用它。 从 Visual Studio 2008 起，浏览信息和符号信息自动存储在解决方案文件夹的 SQL Server .sdf 文件中。

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

有关相关信息，请参阅[BSCMAKE 命令文件](bscmake-command-file-response-file.md)并[BSCMAKE 选项](bscmake-options.md)。

## <a name="see-also"></a>请参阅

[BSCMAKE 参考](bscmake-reference.md)
