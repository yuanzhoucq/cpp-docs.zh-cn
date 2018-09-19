---
title: 链接器工具警告 LNK4104 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4104
dev_langs:
- C++
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6304f3ea928c89f4756a4594270ebb7914324f85
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057257"
---
# <a name="linker-tools-warning-lnk4104"></a>链接器工具警告 LNK4104

导出符号 symbol 应为 PRIVATE

`symbol`可以是以下之一：

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllGetDocumentation`

- `DllInitialize`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllRegisterServerExW`

- `DllUnload`

- `DllUnregisterServer`

- `RasCustomDeleteEntryNotify`

- `RasCustomDial`

- `RasCustomDialDlg`

- `RasCustomEntryDlg`

此警告生成 DLL 导入库时，将发出，而无需指定为专用模块定义文件中导出一个更高版本的函数。 一般情况下，这些函数仅由 OLE 用于导出。 将它们放置在库中导入可能会导致异常行为时错误地链接到库的程序会调用它们。 PRIVATE 关键字的详细信息，请参阅[导出](../../build/reference/exports.md)。