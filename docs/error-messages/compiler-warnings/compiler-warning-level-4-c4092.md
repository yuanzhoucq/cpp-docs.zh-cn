---
title: 编译器警告 （等级 C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: a6949586cf3faa00aafed37a72e58c1b80266cf5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490410"
---
# <a name="compiler-warning-level-4-c4092"></a>编译器警告 （等级 C4092

sizeof 返回 unsigned long

操作数`sizeof`运算符是非常大，因此`sizeof`返回无符号**长**。 在 Microsoft 扩展会出现此警告 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。 在 ANSI 兼容性 (/Za)，而被截断结果。