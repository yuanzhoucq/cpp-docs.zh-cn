---
title: 链接器工具警告 LNK4237 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4237
dev_langs:
- C++
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 479bd4ff8a4f48da679c9e17ec100668de84d089
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113703"
---
# <a name="linker-tools-warning-lnk4237"></a>链接器工具警告 LNK4237

已指定时从 dll; 导入使用 /subsystem: console 或者 /subsystem: windows。

[已](../../build/reference/subsystem-specify-subsystem.md)时生成的 windows (Win32) 应用程序直接使用的一个或多个以下指定：

- Kernel32.dll

- gdi32.dll

- user32.dll

- 一个 msvcrt\* dll。

通过不指定解决此警告**已**。