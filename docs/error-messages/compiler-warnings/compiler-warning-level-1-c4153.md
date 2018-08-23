---
title: 编译器警告 （等级 1） C4153 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4153
dev_langs:
- C++
helpviewer_keywords:
- C4153
ms.assetid: 37a15754-9dba-470b-adda-c4b888064b3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1193bc56b7de45675eb1d09e7c48c19d681119d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276235"
---
# <a name="compiler-warning-level-1-c4153"></a>编译器警告（等级 1）C4153
表达式中的函数/数据指针转换  
  
 在函数指针与数据指针之间转换。 在 Microsoft 扩展 (/Ze) 下允许此类转换，但在 ANSI C 下则不允许。