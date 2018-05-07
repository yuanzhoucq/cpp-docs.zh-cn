---
title: 编译器警告 （等级 1） C4953 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0af5a16ebbf7851eceb2f2cd355f953b14c4bd38
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4953"></a>编译器警告（等级 1）C4953
在收集配置文件数据后已编辑过内联“function”，没有使用配置文件数据  
  
 当使用 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)时，编译器检测到在 `/LTCG:PGINSTRUMENT` 之后重新编译的一个输入模块，该模块具有编辑过的函数 (***function***)，在该模块内，现有测试运行将该函数标识为内联的候选项。 但是，重新编译该模块后，此函数不再是内联的候选项。  
  
 此警告为信息性。 若要解决此警告，请运行 `/LTCG:PGINSTRUMENT`，重做所有测试，并运行 `/LTCG:PGOPTIMIZE`。  
  
 如果已使用 `/LTCG:PGOPTIMIZE` ，此警告将替换为一个错误。