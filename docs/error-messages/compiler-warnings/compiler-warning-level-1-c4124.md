---
title: 编译器警告 （等级 1） C4124 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4124
dev_langs:
- C++
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a69190487c22987ead2d00ec102785ed42ea93c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090919"
---
# <a name="compiler-warning-level-1-c4124"></a>编译器警告 （等级 1） C4124

带有堆栈检查的 __fastcall 是低效的

`__fastcall`关键字用于启用堆栈检查。

`__fastcall`约定生成使代码更快，但堆栈检查会导致速度较慢的代码。 使用时`__fastcall`，关闭堆栈检查与**check_stack**杂注或 /Gs。

仅对在这些情况下声明的第一个函数，将发出此警告。