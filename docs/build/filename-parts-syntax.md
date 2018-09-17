---
title: 文件名部分语法 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5bf7a9685face739059c4b947a5796cc0a28950a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703165"
---
# <a name="filename-parts-syntax"></a>文件名部分语法

在命令中的文件名部分语法表示第一个依赖项文件名 （这可能是暗含的依赖项） 的组件。 文件名组件是文件的驱动器、 路径、 基名称和扩展名，因为它存在于磁盘上。 使用 **%s**表示完整的文件名。 使用 **%&#124;**[*部件*]**F** (竖线后面的百分比符号的字符) 来表示部分文件名，其中*部件*可以是零个或多个以下的字母，按任意顺序。

|Letter|描述|
|------------|-----------------|
|无号|完整名称 (与相同 **%s**)|
|**d**|驱动器|
|**p**|路径|
|**f**|文件基名称|
|**e**|文件扩展名|

例如，如果文件名为 c:\prog.exe:

- 将 c:\prog.exe %s。

- %&#124;将 c:\prog.exe F。

- %&#124;将 c dF。

- %&#124;pF 将是 c:\

- %&#124;将 prog fF。

- %&#124;eF 将 exe

## <a name="see-also"></a>请参阅

[生成文件中的命令](../build/commands-in-a-makefile.md)