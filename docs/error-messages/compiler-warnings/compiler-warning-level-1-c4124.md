---
title: 编译器警告 （等级 1） C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 04732619571420e777244b81bf4b93b775477a20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310976"
---
# <a name="compiler-warning-level-1-c4124"></a>编译器警告 （等级 1） C4124

带有堆栈检查的 __fastcall 是低效的

`__fastcall`关键字用于启用堆栈检查。

`__fastcall`约定生成使代码更快，但堆栈检查会导致速度较慢的代码。 使用时`__fastcall`，关闭堆栈检查与**check_stack**杂注或 /Gs。

仅对在这些情况下声明的第一个函数，将发出此警告。