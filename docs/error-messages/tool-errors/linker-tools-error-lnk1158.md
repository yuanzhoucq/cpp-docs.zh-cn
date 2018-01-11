---
title: "链接器工具错误 LNK1158 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1158
dev_langs: C++
helpviewer_keywords: LNK1158
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 65be945fdb6747b2b47a105051c9e5c37ef532ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1158"></a>链接器工具错误 LNK1158
无法运行 filename  
  
 给定的可执行文件调用[链接](../../build/reference/linker-command-line-syntax.md)既不在包含链接的目录中指定的目录中的 PATH 环境变量。  
  
 例如，将出现此错误，如果你尝试使用的 PGOPTIMIZE 参数[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)具有 32 位操作系统的计算机上的链接器选项。