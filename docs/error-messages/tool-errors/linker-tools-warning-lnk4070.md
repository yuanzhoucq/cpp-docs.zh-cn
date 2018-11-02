---
title: 链接器工具警告 LNK4070
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: e7139b21f053ea8633356c7194cd719a6a4aef35
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622971"
---
# <a name="linker-tools-warning-lnk4070"></a>链接器工具警告 LNK4070

中的 /out: filename 指令。EXP 不同于输出文件名 filename;忽略指令

`filename`中指定[名称](../../build/reference/name-c-cpp.md)或[库](../../build/reference/library.md)语句创建.exp 文件时不同于输出`filename`的已假定默认情况下，或使用指定[/Out](../../build/reference/out-output-file-name.md)选项。

如果更改输出文件在开发环境中并不更新项目的.def 文件的位置的名称，你将看到此警告。 手动更新.def 文件以解决此警告。

使用生成的 DLL 的客户端程序可能会遇到问题。