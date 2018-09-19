---
title: 链接器工具警告 LNK4099 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4099
dev_langs:
- C++
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50bdceaba2e72312febec4819b96df334b5398c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025993"
---
# <a name="linker-tools-warning-lnk4099"></a>链接器工具警告 LNK4099

使用对象/library 或 path; 在未找到 PDB filename正在链接对象，如同没有调试信息一样

链接器无法找到.pdb 文件。 将其复制到目录，其中包含`object/library`。

若要查找的对象文件与关联的.pdb 文件的名称：

1. 从库中提取的对象文件[lib](../../build/reference/lib-reference.md) **/extract:**`objectname`**.obj** `xyz` **.lib**。

1. 检查与.pdb 文件的路径**dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**。

此外可以使用编译[/z7](../../build/reference/z7-zi-zi-debug-information-format.md)，因此不需要使用，或删除 pdb [/debug](../../build/reference/debug-generate-debug-info.md)链接器选项，如果没有要链接的对象的.pdb 文件。