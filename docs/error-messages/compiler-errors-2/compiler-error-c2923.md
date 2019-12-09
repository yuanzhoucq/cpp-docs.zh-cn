---
title: 编译器错误 C2923
ms.date: 11/04/2016
f1_keywords:
- C2923
helpviewer_keywords:
- C2923
ms.assetid: 6b92933b-13ef-4124-99d9-b89f9fdae030
ms.openlocfilehash: 3046d7009d2a54bab6d4d9acf0706335ae9d1974
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761001"
---
# <a name="compiler-error-c2923"></a>编译器错误 C2923

“type”: 对于参数“param”，“identifier”不是有效的模板类型参数

参数列表缺少实例化模板或泛型所需的类型。 检查模板或泛型声明。

下面的示例生成 C2923：

```cpp
// C2923.cpp
template <class T> struct TC {};
int x;
int main() {
   TC<x>* tc2;   // C2923
   TC<int>* tc2;   // OK
}
```

使用泛型时，也可能会发生 C2923：

```cpp
// C2923b.cpp
// compile with: /clr /c
generic <class T> ref struct GC {};

int x;

int main() {
   GC<x>^ gc2;   // C2923
   GC<int>^ gc2;   // OK
}
```
