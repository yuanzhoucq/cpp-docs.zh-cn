---
title: 编译器错误 C3286
ms.date: 11/04/2016
f1_keywords:
- C3286
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
ms.openlocfilehash: 8c09ea34c7dabf2cadecad7c76d766c9496f5a5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461004"
---
# <a name="compiler-error-c3286"></a>编译器错误 C3286

> '*说明符*： 迭代变量不能包含任何存储类说明符

存储类不能对指定的迭代变量。 有关详细信息，请参阅[存储类 （c + +）](../../cpp/storage-classes-cpp.md)并[对于每个，在](../../dotnet/for-each-in.md)。

## <a name="example"></a>示例

下面的示例生成 c3286:，并还显示了正确的使用。

```cpp
// C3286.cpp
// compile with: /clr
int main() {
   array<int> ^p = { 1, 2, 3 };
   for each (static int i in p) {}   // C3286
   for each (int j in p) {}   // OK
}
```