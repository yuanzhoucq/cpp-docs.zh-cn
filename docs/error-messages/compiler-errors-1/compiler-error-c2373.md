---
title: 编译器错误 C2373 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2373
dev_langs:
- C++
helpviewer_keywords:
- C2373
ms.assetid: 7a08bf0b-852d-48be-ba75-70df9f4b5951
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e9b667b733b99a7ae9e1b297ad2557fb55784be
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110362"
---
# <a name="compiler-error-c2373"></a>编译器错误 C2373

“identifier”：重定义；不同的类型修饰符

已使用不同的类型修饰符定义标识符。

下面的示例生成 C2373：

```
// C2373.h
void __clrcall func( void );
const int i = 20;
```

然后：

```
// C2373.cpp
// compile with: /c
#include "C2373.h"
extern void __cdecl func( void );   // C2373
extern void __clrcall func( void );   // OK

extern int i;   // C2373
extern const int i;   // OK
```