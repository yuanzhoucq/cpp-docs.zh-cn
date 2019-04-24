---
title: inline_recursion
ms.date: 11/04/2016
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
ms.openlocfilehash: 80ffabc6ac7c95fd7d9fb4e62bea38c2a04b04f0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026907"
---
# <a name="inlinerecursion"></a>inline_recursion
控制直接或相互递归函数调用的内联扩展。

## <a name="syntax"></a>语法

```
#pragma inline_recursion( [{on | off}] )
```

## <a name="remarks"></a>备注

使用此杂注控制函数标记为[内联](../cpp/inline-functions-cpp.md)并[__inline](../cpp/inline-functions-cpp.md)下自动扩展编译器的函数或`/Ob2`选项。 需要使用此杂注[/Ob](../build/reference/ob-inline-function-expansion.md)编译器选项设置为 1 或 2。 默认状态**inline_recursion**处于关闭状态。 此杂注在出现后在第一个函数调用处生效，并且不会影响函数的定义。

**Inline_recursion**杂注控制如何扩展递归函数。 如果**inline_recursion**被关闭，并且如果内联函数调用自身 （直接或间接），该函数是仅扩展一次。 如果**inline_recursion**处于启用状态，直到它达到设置的值，该函数将扩展多次[inline_depth](../preprocessor/inline-depth.md)杂注，递归函数所定义的默认值`inline_depth`杂注或容量限制。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[inline_depth](../preprocessor/inline-depth.md)<br/>
[/Ob（内联函数展开）](../build/reference/ob-inline-function-expansion.md)