---
title: 编译器警告（等级 1）C4036
ms.date: 11/04/2016
f1_keywords:
- C4036
helpviewer_keywords:
- C4036
ms.assetid: f0b15359-4d62-48ec-8cb1-a7b36587a47f
ms.openlocfilehash: 632e88bb64568c97e937e83e177598054a954f22
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151781"
---
# <a name="compiler-warning-level-1-c4036"></a>编译器警告（等级 1）C4036

未命名的“type”作为实际参数

未向用作实际参数的结构、联合、枚举或类提供任何类型名称。 如果使用 [/Zg](../../build/reference/zg-generate-function-prototypes.md) 来生成函数原型，编译器会发出此警告，并注释掉所生成原型中的形式参数。

指定类型名称，以解决此警告。

## <a name="example"></a>示例

以下示例生成 C4036。

```
// C4036.c
// compile with: /Zg /W1
// D9035 expected
typedef struct { int i; } T;
void f(T* t) {}   // C4036

// OK
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```