---
title: NMAKE 错误 U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: 395f25d8d27bc5e9b6132c87390c8c3bc19b6cc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298238"
---
# <a name="nmake-fatal-error-u1099"></a>NMAKE 错误 U1099

堆栈溢出

正在处理的生成文件已过于复杂，NMAKE 中的当前的堆栈分配。 NMAKE 具有 0x3000 (12 K) 的分配。

若要增加 NMAKE 的堆栈分配，请运行[editbin /stack](../../build/reference/stack.md)实用工具使用更大的堆栈选项：

**editbin /STACK:reserve NMAKE。EXE**

其中*保留*是一个数字大于 NMAKE 中的当前的堆栈分配。