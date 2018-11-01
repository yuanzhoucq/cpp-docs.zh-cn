---
title: 编译器警告 （等级 3） C4316
ms.date: 11/04/2016
f1_keywords:
- C4316
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
ms.openlocfilehash: 5f895a231c8b32d76e4ccd3c15ffae5717d8017f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476058"
---
# <a name="compiler-warning-level-3-c4316"></a>编译器警告 （等级 3） C4316

不可以为此类型对齐在堆上分配的对象。

通过使用分配的过对齐的对象`operator new`可能没有指定的对齐方式。 重写[运算符 new](../../c-runtime-library/operator-new-crt.md)并[运算符 delete](../../c-runtime-library/operator-delete-crt.md)为过对齐类型，以便他们使用的对齐的分配例程 — 例如， [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md)和[_aligned_free](../../c-runtime-library/reference/aligned-free.md)。 下面的示例生成 C4316:

```cpp
// C4316.cpp
// Test: cl /W3 /c C4316.cpp

__declspec(align(32)) struct S {}; // C4324

int main() {
    new S; // C4316
}
```