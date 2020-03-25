---
title: 链接器工具警告 LNK4099
ms.date: 11/04/2016
f1_keywords:
- LNK4099
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
ms.openlocfilehash: b1f330924b8e47e0649268142106a050c83cb20a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183314"
---
# <a name="linker-tools-warning-lnk4099"></a>链接器工具警告 LNK4099

找不到带 "对象/库" 或 "path" 的 PDB "filename";正在链接对象，如同没有调试信息一样

链接器找不到你的 .pdb 文件。 将其复制到包含 `object/library`的目录中。

若要查找与对象文件关联的 .pdb 文件的名称，请执行以下操作：

1. 使用[lib](../../build/reference/lib-reference.md) **/extract：** `objectname``xyz` **.lib**从库中提取对象**文件。**

1. 检查 .pdb 文件的路径，该文件包含**dumpbin/section：. debug $ T/rawdata** `objectname` **.obj**。

你还可以使用[/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)进行编译，以便不需要使用 pdb，或者，如果你要链接的对象没有 .pdb 文件，则删除[/debug](../../build/reference/debug-generate-debug-info.md)链接器选项。
