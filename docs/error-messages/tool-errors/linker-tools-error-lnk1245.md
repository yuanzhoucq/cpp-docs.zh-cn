---
title: 链接器工具错误 LNK1245
ms.date: 11/04/2016
f1_keywords:
- LNK1245
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
ms.openlocfilehash: 4cf9a6c4356872b727a10a360396e51e38928b29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505477"
---
# <a name="linker-tools-error-lnk1245"></a>链接器工具错误 LNK1245

无效的子系统子系统指定任何引用;/SUBSYSTEM 必须是 WINDOWS、 WINDOWSCE 或 CONSOLE

[/clr](../../build/reference/clr-common-language-runtime-compilation.md)用于编译对象和以下条件之一为 true:

- 定义自定义入口点 ([/ENTRY](../../build/reference/entry-entry-point-symbol.md))，以便链接器无法推导出子系统。

- 一个值传递给[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)不能用于 /clr 对象的链接器选项。

对于这两种情况，解决方法是指定于 /SUBSYSTEM 链接器选项的有效值。