---
title: 编译器错误 C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: 18ca9f7d61d96dcc81935bd3563f57bc37da8cd7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228799"
---
# <a name="compiler-error-c3533"></a>编译器错误 C3533

"type"：参数不能具有包含 "auto" 的类型

**`auto`** 如果默认的[/zc： auto](../../build/reference/zc-auto-deduce-variable-type.md)编译器选项有效，则不能使用关键字声明方法或模板参数。

### <a name="to-correct-this-error"></a>更正此错误

1. **`auto`** 从参数声明中删除关键字。

## <a name="example"></a>示例

下面的示例将生成 C3533，因为它使用关键字声明了一个函数参数 **`auto`** ，并使用 **/zc： auto**编译了该参数。

```cpp
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>示例

下面的示例在 c + + 14 模式下生成 C3533，因为它使用关键字声明了一个模板参数 **`auto`** ，并使用 **/zc： auto**编译了该参数。（在 c + + 17 中，这是类模板的有效定义，其中包含一个类型为 "已推导" 的单个非类型模板参数。）

```cpp
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>请参阅

[auto 关键字](../../cpp/auto-keyword.md)<br/>
[/Zc： auto （推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)
