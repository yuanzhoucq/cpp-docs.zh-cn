---
title: "编译器警告 （等级 4） C4092 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4092
dev_langs:
- C++
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6eec21584ec56567b818f23e7dfcf5fb708369ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4092"></a>编译器警告 （等级 4） C4092
sizeof 返回 unsigned long  
  
 操作数`sizeof`运算符已非常大，因此`sizeof`返回无符号**长**。 在 Microsoft 扩展下会出现此警告 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。 在 ANSI 兼容性 (/Za)，则结果将截断相反。