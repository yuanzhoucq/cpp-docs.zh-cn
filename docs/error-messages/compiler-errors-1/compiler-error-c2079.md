---
title: 编译器错误 C2079
ms.date: 11/04/2016
f1_keywords:
- C2079
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
ms.openlocfilehash: 68435610680e3b21415a1d9439a8133fd1e2557f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391954"
---
# <a name="compiler-error-c2079"></a>编译器错误 C2079

identifier 使用未定义的类/结构/联合 name

指定的标识符是未定义的类、 结构或联合。

通过初始化匿名联合可以导致此错误。

下面的示例生成 C2079:

```
// C2079.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   std::ifstream g;   // C2079
}
```

可能的解决方法：

```
// C2079b.cpp
// compile with: /EHsc
#include <fstream>
int main( ) {
   std::ifstream g;
}
```

如果您尝试将对象声明一个仅在作用域中为其前向声明的类型在堆栈上，也可能发生 C2079。

```
// C2079c.cpp
class A;

class B {
   A a;   // C2079
};

class A {};
```

可能的解决方法：

```
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