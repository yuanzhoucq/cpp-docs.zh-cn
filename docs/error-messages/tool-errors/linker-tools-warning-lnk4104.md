---
title: 链接器工具警告 LNK4104
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: 3d89b27c32b33b917abb7fc140eebf5924142423
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298537"
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