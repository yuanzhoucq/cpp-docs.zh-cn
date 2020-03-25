---
title: 编译器警告（等级1） C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 6408185c99a54d5411fa5b1058cd5ec09d3326d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176307"
---
# <a name="compiler-warning-level-1-c4124"></a>编译器警告（等级1） C4124

具有堆栈检查的 __fastcall 效率低下

`__fastcall` 关键字用于启用了堆栈检查。

`__fastcall` 约定生成更快的代码，但堆栈检查会导致代码速度变慢。 使用 `__fastcall`时，请使用**check_stack**杂注或/Gs. 关闭堆栈检查

仅为在这些条件下声明的第一个函数发出此警告。
