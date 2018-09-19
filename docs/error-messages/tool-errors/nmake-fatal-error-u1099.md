---
title: NMAKE 错误 U1099 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1099
dev_langs:
- C++
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3ef75a1435d8c922087fcdd21d1941961bc82cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113378"
---
# <a name="nmake-fatal-error-u1099"></a>NMAKE 错误 U1099

堆栈溢出

正在处理的生成文件已过于复杂，NMAKE 中的当前的堆栈分配。 NMAKE 具有 0x3000 (12 K) 的分配。

若要增加 NMAKE 的堆栈分配，请运行[editbin /stack](../../build/reference/stack.md)实用工具使用更大的堆栈选项：

**editbin /STACK:reserve NMAKE。EXE**

其中*保留*是一个数字大于 NMAKE 中的当前的堆栈分配。