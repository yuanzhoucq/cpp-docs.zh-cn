---
title: 链接器工具错误 LNK1158 |Microsoft 文档
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
ms.openlocfilehash: 71cee2a31d1a7b05104031fbf41e8e3addb82d7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300181"
---
# <a name="linker-tools-error-lnk1158"></a>链接器工具错误 LNK1158
无法运行 filename  
  
 给定的可执行文件调用[链接](../../build/reference/linker-command-line-syntax.md)既不在包含链接的目录中指定的目录中的 PATH 环境变量。  
  
 例如，将出现此错误，如果你尝试使用的 PGOPTIMIZE 参数[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)具有 32 位操作系统的计算机上的链接器选项。