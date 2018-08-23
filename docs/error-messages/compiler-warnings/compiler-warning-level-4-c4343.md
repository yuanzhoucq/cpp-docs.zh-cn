---
title: 编译器警告 （等级 4） C4343 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4343
dev_langs:
- C++
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 300bab652c88322ef7e3b28cbf2cafe304d361d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302329"
---
# <a name="compiler-warning-level-4-c4343"></a>编译器警告（等级 4）C4343
\#杂注 optimize("g",off) 重写 /Og 选项  
  
 此警告（仅在 Itanium 处理器系列 (IPF) 编译器中有效）报告 pragma [optimize](../../preprocessor/optimize.md) 重写 [/Og](../../build/reference/og-global-optimizations.md) 编译器选项。  
  
 下面的示例生成 C4343：  
  
```  
// C4343.cpp  
// compile with: /Og /W4 /LD  
// processor: IPF  
#pragma optimize ("g", off)   // C4343  
```