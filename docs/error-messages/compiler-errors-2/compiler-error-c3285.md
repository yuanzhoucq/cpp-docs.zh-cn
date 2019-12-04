---
title: 编译器错误 C3285
ms.date: 11/04/2016
f1_keywords:
- C3285
helpviewer_keywords:
- C3285
ms.assetid: 04e8f210-d67e-4810-b153-e1efe2986c8f
ms.openlocfilehash: f5799511575617ad1705bbce50a939ee46599628
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755338"
---
# <a name="compiler-error-c3285"></a>编译器错误 C3285

for each 语句不能对“类型”类型的变量进行操作

`for each` 语句针对数组或集合中每个元素重复执行一组嵌入语句。

有关更多信息，请参见 [for each, in](../../dotnet/for-each-in.md) 。

## <a name="example"></a>示例

以下示例生成 C3285.

```cpp
// C3285.cpp
// compile with: /clr
int main() {
   for each (int i in 0) {}   // C3285

   array<int> ^p = { 1, 2, 3 };
   for each (int j in p) {}   // OK
}
```
