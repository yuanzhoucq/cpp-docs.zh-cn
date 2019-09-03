---
title: inline_recursion 杂注
ms.date: 08/29/2019
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
ms.openlocfilehash: 0169e06e8e47f7b0a7b3f73e809ddc988bcf1e95
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220950"
---
# <a name="inline_recursion-pragma"></a>inline_recursion 杂注

控制直接或相互递归函数调用的内联扩展。

## <a name="syntax"></a>语法

> **#pragma inline_recursion (** [{ **on** | **off** }] **)**

## <a name="remarks"></a>备注

使用此杂注控制标记为[inline](../cpp/inline-functions-cpp.md)和[__inline](../cpp/inline-functions-cpp.md)的函数或编译器在`/Ob2`选项下自动扩展的函数。 使用此杂注要求[/Ob](../build/reference/ob-inline-function-expansion.md)编译器选项设置为1或2。 **Inline_recursion**的默认状态为 off。 此杂注在出现杂注后的第一个函数调用处生效, 且不会影响函数的定义。

**Inline_recursion**杂注控制如何扩展递归函数。 如果**inline_recursion**为 off, 并且内联函数直接或间接调用自身, 则只展开一次该函数。 如果**inline_recursion**为 on, 则函数将展开多次, 直到它达到通过[inline_depth](../preprocessor/inline-depth.md)杂注设置的值、由`inline_depth`杂注定义的递归函数的默认值或容量限制。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_depth](../preprocessor/inline-depth.md)\
[/Ob（内联函数展开）](../build/reference/ob-inline-function-expansion.md)
