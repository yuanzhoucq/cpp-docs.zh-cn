---
title: 链接器工具错误 LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 7290a90dfd92d84c4632e7f9dd38d36eccd4ac27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386325"
---
# <a name="linker-tools-error-lnk2020"></a>链接器工具错误 LNK2020

无法解析的标记 token

类似于未定义的外部错误，只不过该引用是通过元数据。 在元数据，必须定义所有函数和数据。

若要解决：

- 定义缺少函数或数据，或

- 包括的对象文件或在其中缺少的函数或数据已定义的库。

## <a name="example"></a>示例

下面的示例生成 LNK2020。

```
// LNK2020.cpp
// compile with: /clr /LD
ref struct A {
   A(int x);   // LNK2020
   static int f();   // LNK2020
};

// OK
ref struct B {
   B(int x) {}
   static int f() { return 0; }
};
```

## <a name="example"></a>示例

如果您创建的变量的一种托管的模板类型，但不是还实例化类型，也会出现 LNK2020。

下面的示例生成 LNK2020。

```
// LNK2020_b.cpp
// compile with: /clr

template <typename T>
ref struct Base {
   virtual void f1() {};
};

template <typename T>
ref struct Base2 {
   virtual void f1() {};
};

int main() {
   Base<int>^ p;   // LNK2020
   Base2<int>^ p2 = gcnew Base2<int>();   // OK
};
```