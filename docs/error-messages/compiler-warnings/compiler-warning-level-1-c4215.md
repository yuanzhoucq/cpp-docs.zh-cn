---
title: 编译器警告 （等级 1） C4215 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4215
dev_langs:
- C++
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 137a278452e9e3e204d761f0519c16541cfdb46e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094086"
---
# <a name="compiler-warning-level-1-c4215"></a>编译器警告（等级 1）C4215

使用了非标准扩展： 长浮点

默认 Microsoft 扩展 (/Ze) 将视为**长浮点**作为**double**。 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 却没有。 使用**double**以保持兼容性。

下面的示例生成 C4215:

```
// C4215.cpp
// compile with: /W1 /LD
long float a;   // C4215

// use the line below to resolve the warning
// double a;
```