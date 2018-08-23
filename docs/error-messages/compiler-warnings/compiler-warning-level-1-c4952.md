---
title: 编译器警告 （等级 1） C4952 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4952
dev_langs:
- C++
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 42696dfae816742c958bca23e25e311e834dd62a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292137"
---
# <a name="compiler-warning-level-1-c4952"></a>编译器警告（等级 1）C4952
“function”：在程序数据库“pgd_file”中未找到配置文件数据  
  
 当使用 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)时，编译器检测到一个在 `/LTCG:PGINSTRUMENT` 后被重新编译且具有一个新的函数 (***function***) 存在的输入模块。  
  
 此警告为信息性。 若要解决此警告，请运行 `/LTCG:PGINSTRUMENT`，重做所有测试，并运行 `/LTCG:PGOPTIMIZE`。  
  
 如果已使用 `/LTCG:PGOPTIMIZE` ，此警告将替换为一个错误。