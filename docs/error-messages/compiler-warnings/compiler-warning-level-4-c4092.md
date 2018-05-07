---
title: 编译器警告 （等级 4） C4092 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4092
dev_langs:
- C++
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ca145addc16306d613817643e363ecd9c95069a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4092"></a>编译器警告 （等级 4） C4092
sizeof 返回 unsigned long  
  
 操作数`sizeof`运算符已非常大，因此`sizeof`返回无符号**长**。 在 Microsoft 扩展下会出现此警告 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。 在 ANSI 兼容性 (/Za)，则结果将截断相反。