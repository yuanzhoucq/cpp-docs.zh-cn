---
title: BSCMAKE 如何生成。Bsc 文件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- browse information files (.bsc), building
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aadf3b29b0714cc47850e177ebe6e1d0e54df784
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719428"
---
# <a name="how-bscmake-builds-a-bsc-file"></a>BSCMAKE 如何生成 .Bsc 文件

BSCMAKE 生成，或以最高效的方式，它可以将重新生成.bsc 文件。 若要避免潜在问题，请务必了解生成过程。

当 BSCMAKE 生成浏览信息文件时，它将截断的.sbr 文件长度为零。 在同一文件的后续的生成，长度为零 （或为空） 的.sbr 文件告知 BSCMAKE 的.sbr 文件有新的发布内容进行。 它允许 BSCMAKE 知道不需要的文件的该部件的更新和将足以增量生成。 在每次生成过程 （除非指定了 /n 选项），BSCMAKE 首先尝试使用已更改那些.sbr 文件以增量方式更新该文件。

BSCMAKE 查找具有与 /o 选项指定的名称的.bsc 文件。 如果未指定 /o，BSCMAKE 查找具有第一个的.sbr 文件和.bsc 扩展的基名称的文件。 如果该文件存在，BSCMAKE 执行使用仅将相关的.sbr 文件的浏览信息文件的增量生成。 如果该文件不存在，BSCMAKE 执行完全生成使用所有的.sbr 文件。 生成的规则如下所示：

- 若要成功执行完整生成、 指定所有的.sbr 文件必须存在，并且不会截断。 如果截断的.sbr 文件，则必须重新生成它 （通过重新编译或组装） 之前运行 BSCMAKE。

- 若要成功执行增量生成，必须存在.bsc 文件。 所有参与的.sbr 文件，甚至是空文件，必须存在并且必须指定 BSCMAKE 命令行上。 如果省略的.sbr 文件从命令行，BSCMAKE 从文件中移除其作品。

## <a name="see-also"></a>请参阅

[生成 .Bsc 文件](../../build/reference/building-a-dot-bsc-file.md)