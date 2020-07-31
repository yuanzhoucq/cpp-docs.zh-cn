---
title: alloc_text 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
ms.openlocfilehash: c638c2026a493453aeb5aff00ba6273efb5f184e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219438"
---
# <a name="alloc_text-pragma"></a>alloc_text 杂注

命名指定的函数定义驻留的代码部分。 杂注必须出现在函数声明符和命名函数的函数定义之间。

## <a name="syntax"></a>语法

> **#pragma alloc_text （** "*textsection*" **，** *function1* [**，** *function2* ] **）**

## <a name="remarks"></a>备注

**Alloc_text**杂注不处理 c + + 成员函数或重载函数。 它仅适用于用 C 链接声明的函数（即，用**extern "C"** 链接规范声明的函数）。 如果尝试对带 C++ 链接的函数使用此杂注，则会生成编译器错误。

由于不支持使用的函数寻址 **`__based`** ，因此，指定节位置需要使用**alloc_text**杂注。 *Textsection*指定的名称应用双引号引起来。

**Alloc_text**杂注必须出现在任何指定函数的声明之后和这些函数的定义之前。

**Alloc_text**杂注中引用的函数应在杂注所在的模块中定义。 否则，如果未定义的函数稍后编译为其他文本部分，则可能会捕获该错误，也可能不会捕获。 尽管此程序通常都会正常运行，但该函数不会在预期部分中分配。

**Alloc_text**的其他限制如下：

- 它不能在函数内使用。

- 必须在声明函数后且在定义函数前使用它。

## <a name="see-also"></a>另请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
