---
title: 编译器错误 C3286
ms.date: 11/04/2016
f1_keywords:
- C3286
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
ms.openlocfilehash: 4c87e98f11a560d0d92be8ea7bc624edd4e09ad2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201391"
---
# <a name="compiler-error-c3286"></a>编译器错误 C3286

> "*说明符*"：迭代变量不能包含任何存储类说明符

不能对迭代变量指定存储类。 有关详细信息，请参阅[中的](../../dotnet/for-each-in.md)[存储C++类（）](../../cpp/storage-classes-cpp.md)和。

## <a name="example"></a>示例

下面的示例生成 C3286，并显示正确的用法。

```cpp
// C3286.cpp
// compile with: /clr
int main() {
   array<int> ^p = { 1, 2, 3 };
   for each (static int i in p) {}   // C3286
   for each (int j in p) {}   // OK
}
```
