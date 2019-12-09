---
title: 编译器错误 C2976
ms.date: 11/04/2016
f1_keywords:
- C2976
helpviewer_keywords:
- C2976
ms.assetid: d9bf9836-325e-4f72-a7e3-a67cf19d32e7
ms.openlocfilehash: 76fd2363b6139bc1bc04aa4d4949a12522e31aa6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751789"
---
# <a name="compiler-error-c2976"></a>编译器错误 C2976

"identifier"：类型参数太少

泛型或模板缺少一个或多个实参。 检查泛型或模板声明，以查找正确的参数数目。

此错误可能是由于标准库组件中C++缺少模板参数引起的。

下面的示例生成 C2976：

```cpp
// C2976.cpp
template <class T>
struct TC {
   T t;
};
int main() {
   TC<>* t;   // C2976
   TC<int>* t2;   // OK
}
```

使用泛型时也可能发生 C2976：

```cpp
// C2976b.cpp
// compile with: /clr
generic <class T>
ref struct GC {
   T t;
};

int main() {
   GC<>^ g;   // C2976
   GC<int>^ g2;   // OK
}
```
