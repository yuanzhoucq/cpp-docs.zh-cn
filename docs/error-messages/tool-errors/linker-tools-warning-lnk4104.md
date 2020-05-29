---
title: 链接器工具警告 LNK4104
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: 604dccf01b3dffc0060546bebf19d64c16ebf965
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193961"
---
# <a name="linker-tools-warning-lnk4104"></a>链接器工具警告 LNK4104

符号 "symbol" 的导出应为私有

`symbol` 可以是以下项之一：

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

在为 DLL 生成导入库时，将发出此警告，并导出上述函数之一，而不在模块定义文件中将其指定为私有。 通常，这些函数仅供 OLE 使用。 如果链接到库的程序不正确地调用它们，则将它们放入导入库可能导致异常行为。 有关 PRIVATE 关键字的详细信息，请参阅[导出](../../build/reference/exports.md)。
