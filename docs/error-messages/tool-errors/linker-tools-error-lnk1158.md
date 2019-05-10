---
title: 链接器工具错误 LNK1158
ms.date: 11/04/2016
f1_keywords:
- LNK1158
helpviewer_keywords:
- LNK1158
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
ms.openlocfilehash: 0dbb40fb1fe0405f3685a5e7246ecba2b53ec526
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62254948"
---
# <a name="linker-tools-error-lnk1158"></a>链接器工具错误 LNK1158

无法运行 filename

调用给定的可执行文件[链接](../../build/reference/linking.md)不在包含链接的目录，也不在路径环境变量中指定的目录中。

例如，你将收到此错误，如果你尝试使用 PGOPTIMIZE 参数来[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)具有 32 位操作系统的计算机上的链接器选项。