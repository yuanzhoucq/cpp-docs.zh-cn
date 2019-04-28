---
title: /REBASE
ms.date: 11/04/2016
f1_keywords:
- /rebase
helpviewer_keywords:
- base addresses [C++]
- -REBASE editbin option
- REBASE editbin option
- DLLs [C++], linking
- executable files [C++], base address
- /REBASE editbin option [C++]
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
ms.openlocfilehash: 42cbcb911fcd0aa7753d84aae5523d28371b9972
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319195"
---
# <a name="rebase"></a>/REBASE

```
/REBASE[:modifiers]
```

## <a name="remarks"></a>备注

此选项设置为指定的文件的基址。 EDITBIN 将分配新的基址，根据大小接近的 64 KB 向上舍入为每个文件的连续地址空间中。 有关基址的详细信息，请参阅[基址](base-base-address.md)（/ 基） 链接器选项。

指定的程序可执行文件和中的 Dll*文件*它们是以数据为基础的顺序在 EDITBIN 命令行参数。 您可以选择指定一个或多个*修饰符*，每个由逗号分隔 (**，**):

|修饰符|操作|
|--------------|------------|
|**BASE=**<em>address</em>|为重新分配到文件的基址提供起始地址。 指定*地址*以十进制或 C 语言表示法。 如果未指定基本，默认开始基址是 0x400000 处。 必须指定如果列表是使用的基础，并*地址*设置基址的范围的末尾。|
|**BASEFILE**|创建一个名为 COFFBASE 文件。TXT，这是一个文本文件中链接的所需的格式/基本选项。|
|**向下**|告知 EDITBIN 重新分配基址向下的从结束地址。 使用下面的地址范围末尾的最高可能地址中的第一个文件指定的顺序重新分配文件。 基本必须使用与列表以确保足够的地址空间并且将这些文件。 若要确定由指定的文件所需的地址空间，运行 /REBASE EDITBIN 的文件，并将 64KB 添加到显示的总大小。|

## <a name="see-also"></a>请参阅

[EDITBIN 选项](editbin-options.md)
