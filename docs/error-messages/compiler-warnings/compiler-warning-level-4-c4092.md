---
title: 编译器警告 （等级 C4092 |Microsoft Docs
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
ms.openlocfilehash: 84aa73120dabd261d54e764d1e0bfe8bc9c561a0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039596"
---
# <a name="compiler-warning-level-4-c4092"></a>编译器警告 （等级 C4092

sizeof 返回 unsigned long

操作数`sizeof`运算符是非常大，因此`sizeof`返回无符号**长**。 在 Microsoft 扩展会出现此警告 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。 在 ANSI 兼容性 (/Za)，而被截断结果。