---
title: 链接器工具警告 LNK4070 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4070
dev_langs:
- C++
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cfb4ae1c5440742c491d9615a2b4929a9b04f66
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106929"
---
# <a name="linker-tools-warning-lnk4070"></a>链接器工具警告 LNK4070

中的 /out: filename 指令。EXP 不同于输出文件名 filename;忽略指令

`filename`中指定[名称](../../build/reference/name-c-cpp.md)或[库](../../build/reference/library.md)语句创建.exp 文件时不同于输出`filename`的已假定默认情况下，或使用指定[/Out](../../build/reference/out-output-file-name.md)选项。

如果更改输出文件在开发环境中并不更新项目的.def 文件的位置的名称，你将看到此警告。 手动更新.def 文件以解决此警告。

使用生成的 DLL 的客户端程序可能会遇到问题。