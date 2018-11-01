---
title: 编译器错误 C2190
ms.date: 11/04/2016
f1_keywords:
- C2190
helpviewer_keywords:
- C2190
ms.assetid: 34e15f85-d979-4948-80fc-46c414508a70
ms.openlocfilehash: b52797b945b1a652506b4a85171e60a91544bbf0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546466"
---
# <a name="compiler-error-c2190"></a>编译器错误 C2190

第一个参数列表比第二个长

在第二个时间内使用较短的参数列表声明了 C 函数。 C 不支持重载的函数。

下面的示例生成 C2190:

```
// C2190.c
// compile with: /Za /c
void func( int, float );
void func( int  );   // C2190, different parameter list
void func2( int  );   // OK
```