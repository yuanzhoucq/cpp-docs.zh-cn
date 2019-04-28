---
title: 链接器工具警告 LNK4237
ms.date: 11/04/2016
f1_keywords:
- LNK4237
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
ms.openlocfilehash: 62ce0a0edc7f15bc5a19e4630133976f413da35a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352653"
---
# <a name="linker-tools-warning-lnk4237"></a>链接器工具警告 LNK4237

已指定时从 dll; 导入使用 /subsystem: console 或者 /subsystem: windows。

[已](../../build/reference/subsystem-specify-subsystem.md)时生成的 windows (Win32) 应用程序直接使用的一个或多个以下指定：

- Kernel32.dll

- gdi32.dll

- user32.dll

- 一个 msvcrt\* dll。

通过不指定解决此警告**已**。