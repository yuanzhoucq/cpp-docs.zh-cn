---
title: conform
ms.date: 11/04/2016
f1_keywords:
- conform_CPP
- vc-pragma.conform
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
ms.openlocfilehash: 35c3b06106779a9056f682ff76c6ed4b4ab1ab41
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026573"
---
# <a name="conform"></a>conform
**C++特定**

指定的运行时行为[/zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)编译器选项。

## <a name="syntax"></a>语法

> **#pragma conform(** *name* [**, show** ] [**,** { **on** | **off** } ] [ [**,** { **push** | **pop** } ] [**,** *identifier* ] ] **)**

### <a name="parameters"></a>参数

*name*<br/>
指定要修改的编译器选项的名称。 唯一有效*名称*是`forScope`。

**show**<br/>
（可选）当前设置将导致*名称*（true 或 false） 在编译期间显示通过一条警告消息。 例如 `#pragma conform(forScope, show)`。

**上**，**关闭**<br/>
（可选）设置*名称*到**上**使[/zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)编译器选项。 默认值是**关闭**。

**push**<br/>
（可选）将当前值推送*名称*到内部编译器堆栈上。 如果指定*标识符*，可以指定**上**或**关闭**值*名称*可以被推送到堆栈上。 例如 `#pragma conform(forScope, push, myname, on)`。

**pop**<br/>
（可选）设置的值*名称*到内部编译器堆栈和弹出堆栈的顶部的值。 如果具有指定标识符**pop**，堆栈将弹回，直到它找到的记录*标识符*，这也会弹出; 的当前值*名称*中在堆栈上的下一个记录成为的新值*名称*。 如果指定**pop**与*标识符*不在堆栈上，一条记录中**pop**将被忽略。

*identifier*<br/>
（可选）可随附**推送**或**pop**命令。 如果*标识符*使用，则**上**或**关闭**还可以使用说明符。

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

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)