---
title: 链接器工具警告 LNK4099
ms.date: 11/04/2016
f1_keywords:
- LNK4099
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
ms.openlocfilehash: dcf4d44c3a0b5b10035af763040c2912afc8c6f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310885"
---
# <a name="linker-tools-warning-lnk4099"></a>链接器工具警告 LNK4099

使用对象/library 或 path; 在未找到 PDB filename正在链接对象，如同没有调试信息一样

链接器无法找到.pdb 文件。 将其复制到目录，其中包含`object/library`。

若要查找的对象文件与关联的.pdb 文件的名称：

1. 从库中提取的对象文件[lib](../../build/reference/lib-reference.md) **/extract:**`objectname`**.obj** `xyz` **.lib**。

1. 检查与.pdb 文件的路径**dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**。

此外可以使用编译[/z7](../../build/reference/z7-zi-zi-debug-information-format.md)，因此不需要使用，或删除 pdb [/debug](../../build/reference/debug-generate-debug-info.md)链接器选项，如果没有要链接的对象的.pdb 文件。