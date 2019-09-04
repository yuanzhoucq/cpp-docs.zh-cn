---
title: conform 杂注
ms.date: 08/29/2019
f1_keywords:
- conform_CPP
- vc-pragma.conform
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
ms.openlocfilehash: 816ff85bb19f549c6ea072073bd89fcd503545f2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220497"
---
# <a name="conform-pragma"></a>conform 杂注

**C++相关**

指定[/zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)编译器选项的运行时行为。

## <a name="syntax"></a>语法

> **#pragma 符合 (** *name* [ **, show** ] [ **,** { **on** | **off** }] [[ **,** { **push** | **pop** }] [ **,** *标识符*[ **,** { **on** **off}** ]  | ] ] **)**

### <a name="parameters"></a>参数

*路径名*\
指定要修改的编译器选项的名称。 唯一有效的*名称*为`forScope`。

**向**\
可有可无导致在编译过程中通过警告消息显示*名称*(true 或 false) 的当前设置。 例如， `#pragma conform(forScope, show)` 。

**打开**、**关闭**\
可有可无将*名称*设置为**on**可启用[/zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)编译器选项。 默认值为**off**。

**请求**\
可有可无将*名称*的当前值推送到内部编译器堆栈上。 如果指定 "*标识符*", 则可以为要推送到堆栈上的*名称*指定 "**开**" 或 "**关**" 值。 例如， `#pragma conform(forScope, push, myname, on)` 。

**弹出**\
可有可无将*name*的值设置为内部编译器堆栈顶部的值, 然后弹出堆栈。 如果用**pop**指定了标识符, 则会弹出堆栈, 直到找到具有*标识符*的记录, 该记录也会被弹出;堆栈中的下一条记录的*名称*的当前值将成为*name*的新值。 如果指定**pop**时使用的*标识符*不在堆栈上的记录中, 则将忽略**pop** 。

*标志*\
可有可无可以包含**推送**或**弹出**命令。 如果使用了*标识符*, 则也可以使用**on**或**off**说明符。

## <a name="example"></a>示例

```cpp
// pragma_directive_conform.cpp
// compile with: /W1
// C4811 expected
#pragma conform(forScope, show)
#pragma conform(forScope, push, x, on)
#pragma conform(forScope, push, x1, off)
#pragma conform(forScope, push, x2, off)
#pragma conform(forScope, push, x3, off)
#pragma conform(forScope, show)
#pragma conform(forScope, pop, x1)
#pragma conform(forScope, show)

int main() {}
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
