---
title: 编译器警告 （等级 4） C4152 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4152
dev_langs:
- C++
helpviewer_keywords:
- C4152
ms.assetid: 6025ab70-d7cf-4730-913a-3ca0b1186a3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: faa258b7dbd965f0aaa76d4b60bb5c043df1187f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291159"
---
# <a name="compiler-warning-level-4-c4152"></a>编译器警告（等级 4）C4152
非标准扩展, 表达式中的函数/数据指针转换  
  
 在函数指针与数据指针之间转换。 在 Microsoft 扩展 (/Ze) 下允许此类转换，但在 ANSI C 下则不允许。