---
title: 编译器错误 C2079
ms.date: 11/04/2016
f1_keywords:
- C2079
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
ms.openlocfilehash: ea158d8dada013f6b90d0fbe1e7502665c1c24da
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757717"
---
# <a name="compiler-error-c2079"></a>编译器错误 C2079

"identifier" 使用未定义的类/结构/联合 "name"

指定的标识符是未定义的类、结构或联合。

此错误的原因可能是初始化匿名联合。

下面的示例生成 C2079：

```cpp
// C2079.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   std::ifstream g;   // C2079
}
```

可能的解决方法：

```cpp
// C2079b.cpp
// compile with: /EHsc
#include <fstream>
int main( ) {
   std::ifstream g;
}
```

如果你尝试在类型的堆栈上声明一个对象，而该类型的前向声明仅位于范围内，则也可能会发生 C2079。

```cpp
// C2079c.cpp
class A;

class B {
   A a;   // C2079
};

class A {};
```

可能的解决方法：

```cpp
// C2079d.cpp
// compile with: /c
class A;
class C {};

class B {
   A * a;
   C c;
};

class A {};
```
