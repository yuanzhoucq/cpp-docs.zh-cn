---
title: 链接器工具错误 LNK1158
ms.date: 11/04/2016
f1_keywords:
- LNK1158
helpviewer_keywords:
- LNK1158
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
ms.openlocfilehash: f2e3e1d9948960beed631861c5981f2d09daf632
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455934"
---
# <a name="linker-tools-error-lnk1158"></a>链接器工具错误 LNK1158

无法运行 filename

调用给定的可执行文件[链接](../../build/reference/linker-command-line-syntax.md)不在包含链接的目录，也不在路径环境变量中指定的目录中。

例如，你将收到此错误，如果你尝试使用 PGOPTIMIZE 参数来[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)具有 32 位操作系统的计算机上的链接器选项。