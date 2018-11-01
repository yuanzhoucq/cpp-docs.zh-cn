---
title: 错误 C1052
ms.date: 05/08/2017
f1_keywords:
- C1052
helpviewer_keywords:
- C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
ms.openlocfilehash: b381cc3cfe27d4c4a9d744a6b854a0e43727fe71
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479763"
---
# <a name="fatal-error-c1052"></a>错误 C1052

> 程序数据库文件*文件名*，由带 /debug: fastlink; 链接器生成的编译器无法更新此类 PDB 文件; 请删除它或使用 /Fd 来指定不同的 PDB 文件名

编译器无法更新由链接器生成的同一个程序数据库 (PDB) 文件时[/debug: fastlink](../../build/reference/debug-generate-debug-info.md)指定选项。 通常情况下，编译器生成的 PDB 文件和链接器生成的 PDB 文件具有不同的名称。 但是，如果它们设置为使用相同的名称，可以导致此错误。

若要解决此问题，可以显式删除 PDB 文件之前再次，编译，也可以创建不同的编译器生成和链接器生成的 PDB 文件的名称。

若要在命令行上指定的编译器生成的 PDB 文件名称，请使用[/Fd](../../build/reference/fd-program-database-file-name.md)编译器选项。 若要在 IDE 中指定的编译器生成的 PDB 文件名称，打开**属性页**用于你的项目，并在对话框**配置属性**， **C/c + +**， **输出文件**页上，设置**程序数据库文件名**属性。 默认情况下，此属性是`$(IntDir)vc$(PlatformToolsetVersion).pdb`。

或者，可以设置链接器生成的 PDB 文件名称。 若要在命令行上指定链接器生成的 PDB 文件名称，请使用[/PDB](../../build/reference/pdb-use-program-database.md)链接器选项。 若要在 IDE 中指定链接器生成的 PDB 文件名称，打开**属性页**用于你的项目，并在对话框**配置属性**，**链接器**， **调试**页上，设置**生成程序数据库文件**属性。 默认情况下，此属性设置为 `$(OutDir)$(TargetName).pdb`。
