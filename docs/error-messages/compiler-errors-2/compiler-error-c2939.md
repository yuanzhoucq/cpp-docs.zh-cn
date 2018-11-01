---
title: 编译器错误 C2939
ms.date: 11/04/2016
f1_keywords:
- C2939
helpviewer_keywords:
- C2939
ms.assetid: 455b050b-f2dc-4b5b-bd6a-e1f81d3d1644
ms.openlocfilehash: 59b2f63ba12a644f13b3586fbf6eec4d5bfa8be5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604186"
---
# <a name="compiler-error-c2939"></a>编译器错误 C2939

“class”：type-class-id 重新定义为局部数据变量

不能将泛型或模板类用作局部数据变量。

如果大括号匹配不正确，则可能导致此错误。

下面的示例生成 C2939：

```
// C2939.cpp
template<class T>
struct TC { };
int main() {
   int TC<int>;   // C2939
   int TC;   // OK
}
```

使用 generic 时，也可能发生 C2939：

```
// C2939b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };

int main() {
   int GC<int>;   // C2939
   int GC;   // OK
}
```