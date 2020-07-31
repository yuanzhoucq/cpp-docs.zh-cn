---
title: inline_depth 杂注
ms.date: 08/29/2019
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
ms.openlocfilehash: 73540ec19c4ecc18a740dace0d23a37ad43182c0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219412"
---
# <a name="inline_depth-pragma"></a>inline_depth 杂注

指定内联启发式搜索深度。 如果调用关系图中的函数深度超出了指定的值，则不会内联。

## <a name="syntax"></a>语法

> **#pragma inline_depth （** [ *n* ] **）**

## <a name="remarks"></a>备注

此杂注控制标记为[inline](../cpp/inline-functions-cpp.md)和[__inline](../cpp/inline-functions-cpp.md)的函数的内联，或在选项下自动内联 `/Ob` 。

*n*可以是0到255之间的值，其中255表示调用关系图中的深度不受限制。 值0会禁止内联展开。 如果未指定*n* ，则使用默认值254。

**Inline_depth**杂注控制可以扩展一系列函数调用的次数。 例如，假定内联深度为4。 如果 A 调用 B，然后 B 调用 C，则所有三个调用都将以内联方式展开。 但是，如果最近的内联深度展开为2，则只展开 A 和 B，C 将保留为函数调用。

若要使用此杂注，必须将 `/Ob` 编译器选项设置为1或更高。 使用该杂注的深度设置在该杂注后进行第一个函数调用时生效。

内联深度可以在扩展期间减少，但不会增加。 如果内联深度为6，在扩展期间，预处理器遇到值为8的**inline_depth**杂注，深度仍为6。

**Inline_depth**杂注对标记为的函数不起作用 **`__forceinline`** 。

> [!NOTE]
> 可对递归函数进行内联替换，最大调用深度为 16。

## <a name="see-also"></a>另请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_recursion](../preprocessor/inline-recursion.md)
