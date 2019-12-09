---
title: 编译器错误 C2939
ms.date: 11/04/2016
f1_keywords:
- C2939
helpviewer_keywords:
- C2939
ms.assetid: 455b050b-f2dc-4b5b-bd6a-e1f81d3d1644
ms.openlocfilehash: 97aa24eccb5cec7d74f7f7660260fa8b5f6d8d7d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754610"
---
# <a name="compiler-error-c2939"></a>编译器错误 C2939

“class”：type-class-id 重新定义为局部数据变量

不能将泛型或模板类用作局部数据变量。

如果大括号匹配不正确，则可能导致此错误。

下面的示例生成 C2939：

```cpp
// C2939.cpp
template<class T>
struct TC { };
int main() {
   int TC<int>;   // C2939
   int TC;   // OK
}
```

使用 generic 时，也可能发生 C2939：

```cpp
// C2939b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };

int main() {
   int GC<int>;   // C2939
   int GC;   // OK
}
```
