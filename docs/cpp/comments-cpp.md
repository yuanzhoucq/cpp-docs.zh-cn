---
title: 注释 （C++）
ms.date: 11/04/2016
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
ms.openlocfilehash: 3326ad7d0b5118182a5d582061fd0c103986f232
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189749"
---
# <a name="comments-c"></a>注释 （C++）

注释是编译器忽略但对于程序员非常有用的文本。 注释通常用于批注代码以供将来参考。 编译器会将它们视为空白。 您可以使用测试中的注释来使某些代码行处于非活动状态;但是，`#if`/`#endif` 预处理器指令的工作效果更好，因为你可以包围包含注释的代码，但不能嵌套注释。

通过以下方式之一是编写 C++ 注释：

- `/*` （斜杠，星号）字符，后跟任何字符序列（包括新行），后跟 `*/` 个字符。 此语法与 ANSI C 相同。

- `//` （两个斜杠）字符，后跟任何字符序列。 不紧跟在反斜杠之前的新行会终止这种形式的注释。 因此，它通常称为 "单行注释"。

注释字符（`/*`、`*/`和 `//`）在字符常量、字符串文本或注释中没有特殊含义。 使用第一个语法的注释无法嵌套。

## <a name="see-also"></a>另请参阅

[词法约定](../cpp/lexical-conventions.md)
