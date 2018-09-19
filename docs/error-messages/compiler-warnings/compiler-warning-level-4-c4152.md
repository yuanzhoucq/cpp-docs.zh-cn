---
title: 编译器警告 （等级 C4152 |Microsoft Docs
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
ms.openlocfilehash: cab4d812c91239f277dbacede6db43f669908b0a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099624"
---
# <a name="compiler-warning-level-4-c4152"></a>编译器警告（等级 4）C4152

非标准扩展, 表达式中的函数/数据指针转换

在函数指针与数据指针之间转换。 在 Microsoft 扩展 (/Ze) 下允许此类转换，但在 ANSI C 下则不允许。