---
title: 链接器工具警告 LNK4070
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: 391a477625b51fd37eacc5d455801ce90d2abbc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194000"
---
# <a name="linker-tools-warning-lnk4070"></a>链接器工具警告 LNK4070

/OUT：中的 filename 指令。EXP 不同于输出文件名 "filename";正在忽略指令

创建 .exp 文件时在[NAME](../../build/reference/name-c-cpp.md)或[LIBRARY](../../build/reference/library.md)语句中指定的 `filename` 不同于默认情况下假设或使用[/out](../../build/reference/out-output-file-name.md)选项指定的输出 `filename`。

如果在开发环境中更改了输出文件的名称，但未更新项目的 .def 文件，则会看到此警告。 手动更新 .def 文件以解决此警告。

使用生成的 DLL 的客户端程序可能会遇到问题。
