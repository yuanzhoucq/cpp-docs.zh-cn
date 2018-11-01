---
title: 编译器错误 C2719
ms.date: 11/04/2016
f1_keywords:
- C2719
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
ms.openlocfilehash: d635601fbf8b36218fb47c09444f3f5d023c823e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653110"
---
# <a name="compiler-error-c2719"></a>编译器错误 C2719

“parameter”：不对齐具有 __declspec(align('#')) 的形参

[对齐](../../cpp/align-cpp.md)`__declspec`函数参数上不允许使用修饰符。 函数参数的对齐方式由所使用的调用约定控制。 有关详细信息，请参阅[调用约定](../../cpp/calling-conventions.md)。

以下示例将生成 C2719，并演示如何修复此错误：

```
// C2719.cpp
void func(int __declspec(align(32)) i);   // C2719
// try the following line instead
// void func(int i);
```