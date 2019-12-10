---
title: 链接器工具警告 LNK4248
ms.date: 11/04/2016
f1_keywords:
- LNK4248
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
ms.openlocfilehash: 4ba05ef067c539dc9c0aca6dc2a395748fd217a2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988098"
---
# <a name="linker-tools-warning-lnk4248"></a>链接器工具警告 LNK4248

"type" 的无法解析的 typeref 标记（标记）;映像可能无法运行

类型在 MSIL 元数据中没有定义。

当 MSIL 模块中只有一个类型的前向声明（使用 **/clr**编译）时，可能会发生 LNK4248，其中，在 msil 模块中引用了该类型，并且 msil 模块与具有该类型的定义的本机模块关联。

在这种情况下，链接器将在 MSIL 元数据中提供本机类型定义，这可能会提供正确的行为。

但是，如果转发类型声明为 CLR 类型，则链接器的本机类型定义可能不正确

有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

### <a name="to-correct-this-error"></a>更正此错误

1. 提供 MSIL 模块中的类型定义。

## <a name="example"></a>示例

下面的示例生成 LNK4248。 定义要解析的结构 A。

```cpp
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

下面的示例具有类型的前向定义。

```cpp
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

```cpp
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
