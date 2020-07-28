---
title: 编译器警告（等级1） C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 59860bef108a3cd3e8bbbc6ff0790e17dbdaa0d4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214485"
---
# <a name="compiler-warning-level-1-c4124"></a>编译器警告（等级1） C4124

具有堆栈检查的 __fastcall 效率低下

**`__fastcall`** 关键字用于启用堆栈检查。

该 **`__fastcall`** 约定生成更快的代码，但堆栈检查会导致代码较慢。 使用时 **`__fastcall`** ，请使用**check_stack**杂注或/Gs. 关闭堆栈检查

仅为在这些条件下声明的第一个函数发出此警告。
