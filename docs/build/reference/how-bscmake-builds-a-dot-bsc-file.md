---
title: BSCMAKE 如何生成。Bsc 文件 |Microsoft 文档
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
ms.openlocfilehash: 0cdc8a2840e3beb1272b33b2794f70a979684f46
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373483"
---
# <a name="how-bscmake-builds-a-bsc-file"></a>BSCMAKE 如何生成 .Bsc 文件
BSCMAKE 生成或重新生成，以最高效的方式，它可以在.bsc 文件。 若要避免潜在问题，务必了解生成过程。  
  
 当 BSCMAKE 生成浏览信息文件时，它将截断为零长度的.sbr 文件。 在同一文件的后续生成，期间长度为零 （或空） 的.sbr 文件告诉 BSCMAKE.sbr 文件有以使任何新发布内容。 它可让 BSCMAKE 知道不需要的文件的该部分更新和增量生成就够用了。 在每次生成过程 （除非指定了 /n 选项），BSCMAKE 第一次尝试使用已更改那些.sbr 文件以增量方式更新文件。  
  
 BSCMAKE 查找.bsc 文件具有与 /o 选项指定的名称。 如果未指定 /o，BSCMAKE 查找具有的基名称的第一个的.sbr 文件且扩展名为.bsc 文件。 如果该文件存在，则 BSCMAKE 执行使用仅将相关的.sbr 文件的浏览信息文件的增量生成。 如果文件不存在，则 BSCMAKE 执行完全生成使用所有的.sbr 文件。 对于生成的规则如下所示：  
  
-   若要成功执行完整生成、 所有指定.sbr 文件必须存在并且不会被截断。 如果被截断的.sbr 文件，你必须重新生成 （通过重新编译或汇编） 之前运行 BSCMAKE。  
  
-   若要成功执行为增量生成，必须存在.bsc 文件。 所有相关的.sbr 文件，即使空文件，必须存在并且必须 BSCMAKE 命令行上指定。 如果省略的.sbr 文件从命令行，BSCMAKE 从文件中删除它的贡献。  
  
## <a name="see-also"></a>请参阅  
 [生成 .Bsc 文件](../../build/reference/building-a-dot-bsc-file.md)