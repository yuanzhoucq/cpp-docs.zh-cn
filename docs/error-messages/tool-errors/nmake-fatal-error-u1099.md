---
title: NMAKE 错误 U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: c963180059a48d9aa0b09103df1ed54f82b8a2f1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193389"
---
# <a name="nmake-fatal-error-u1099"></a>NMAKE 错误 U1099

堆栈溢出

正在处理的生成文件对于 NMAKE 中当前堆栈分配过于复杂。 NMAKE 分配了0x3000 （12K）。

若要增加 NMAKE 的堆栈分配，请使用更大的堆栈选项运行[editbin/stack](../../build/reference/stack.md)实用工具：

**editbin/STACK：保留 NMAKE.EXE**

其中， *reserve*是大于 NMAKE 中当前堆栈分配的数字。
