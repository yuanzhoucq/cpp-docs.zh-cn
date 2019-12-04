---
title: 编译器错误 C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: ce95bba417e9be3603f15376a0fd65a48f951a2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755637"
---
# <a name="compiler-error-c3533"></a>编译器错误 C3533

"type"：参数不能具有包含 "auto" 的类型

如果默认的[/zc： auto](../../build/reference/zc-auto-deduce-variable-type.md)编译器选项有效，则不能使用 `auto` 关键字声明方法或模板参数。

### <a name="to-correct-this-error"></a>更正此错误

1. 从参数声明中删除 `auto` 关键字。

## <a name="example"></a>示例

下面的示例将生成 C3533，因为它使用 `auto` 关键字声明函数参数，并使用 **/zc： auto**进行编译。

```cpp
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>示例

下面的示例在 c + + 14 模式下生成 C3533，因为它使用 `auto` 关键字声明模板参数，并使用 **/zc： auto**进行编译。（在 c + + 17 中，这是类模板的有效定义，其中包含一个类型为 "已推导" 的单个非类型模板参数。）

```cpp
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>另请参阅

[auto 关键字](../../cpp/auto-keyword.md)<br/>
[/Zc:auto（推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)
