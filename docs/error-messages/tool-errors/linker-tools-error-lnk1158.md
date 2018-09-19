---
title: 链接器工具错误 LNK1158 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1158
dev_langs:
- C++
helpviewer_keywords:
- LNK1158
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ce319aa4529c74cad00342b09aa0ed98bb49ce7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094164"
---
# <a name="linker-tools-error-lnk1158"></a>链接器工具错误 LNK1158

无法运行 filename

调用给定的可执行文件[链接](../../build/reference/linker-command-line-syntax.md)不在包含链接的目录，也不在路径环境变量中指定的目录中。

例如，你将收到此错误，如果你尝试使用 PGOPTIMIZE 参数来[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)具有 32 位操作系统的计算机上的链接器选项。