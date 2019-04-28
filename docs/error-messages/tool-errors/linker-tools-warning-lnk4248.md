---
title: 链接器工具警告 LNK4248
ms.date: 11/04/2016
f1_keywords:
- LNK4248
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
ms.openlocfilehash: db9432c505b7348c9bef5ed34aac1cb4edecb17b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352511"
---
# <a name="linker-tools-warning-lnk4248"></a>链接器工具警告 LNK4248

type; 无法解析的 typeref 标记 （令牌）映像可能无法运行

一种类型在 MSIL 元数据中没有一个定义。

前向声明的 MSIL 模块中的类型时，可以发生 LNK4248 (使用编译 **/clr**)、 在 MSIL 模块中，引用类型和 MSIL 模块链接到包含具有定义的本机模块类型。

在此情况下，链接器将提供的本机类型定义中的 MSIL 元数据，以及这可能提供正确的行为。

但是，如果转发类型声明为 CLR 类型，则链接器的本机类型定义可能不正确

有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

### <a name="to-correct-this-error"></a>更正此错误

1. 提供的 MSIL 模块中的类型定义。

## <a name="example"></a>示例

下面的示例生成 LNK4248。 定义结构 A 来解决。

```
// LNK4248.cpp
// compile with: /clr /W1
// LNK4248 expected
struct A;
void Test(A*){}

int main() {
   Test(0);
}
```

## <a name="example"></a>示例

下面的示例具有一种类型的前向定义。

```
// LNK4248_2.cpp
// compile with: /clr /c
class A;   // provide a definition for A here to resolve
A * newA();
int valueA(A * a);

int main() {
   A * a = newA();
   return valueA(a);
}
```

## <a name="example"></a>示例

下面的示例生成 LNK4248。

```
// LNK4248_3.cpp
// compile with: /c
// post-build command: link LNK4248_2.obj LNK4248_3.obj
class A {
public:
   int b;
};

A* newA() {
   return new A;
}

int valueA(A * a) {
   return (int)a;
}
```