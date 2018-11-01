---
title: 编译器错误 C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: 59ceea942d9165f6f7c6161032e96404bc0dcba7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547246"
---
# <a name="compiler-error-c3533"></a>编译器错误 C3533

type： 参数不能包含 auto 的类型

不能使用声明的方法或模板参数`auto`关键字如果默认值[/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md)编译器选项。

### <a name="to-correct-this-error"></a>更正此错误

1. 删除`auto`关键字从参数声明。

## <a name="example"></a>示例

下面的示例生成 C3533，因为它声明的函数参数`auto`关键字和它与编译 **/zc: auto**。

```
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>示例

下面的示例在 C + + 14 模式下生成 C3533，因为它声明的模板参数`auto`关键字和它与编译 **/zc: auto**。（在 C + + 17，这是具有单个非类型模板参数推导其类型的类模板的有效定义。）

```
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>请参阅

[auto 关键字](../../cpp/auto-keyword.md)<br/>
[/Zc:auto（推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)
