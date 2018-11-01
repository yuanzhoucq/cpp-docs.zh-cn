---
title: 注释 （C++）
ms.date: 11/04/2016
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
ms.openlocfilehash: a90d9d37e69cb2e8be4ab18f77026fdce1221307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506101"
---
# <a name="comments-c"></a>注释 （C++）

注释是的文本，则编译器将忽略，但这是适用于程序员。 注释通常用于批注代码，以供将来参考。 编译器将它们视为空白区域。 您可以使用在测试中的注释以使某些行代码处于非活动状态;但是， `#if` / `#endif`预处理器指令的工作更好地为此因为可环绕包含注释的代码，但不能嵌套注释。

通过以下方式之一是编写 C++ 注释：

- `/*`正斜杠 (星号） 字符后, 跟的字符 （包括新行） 后, 跟任意序列`*/`字符。 此语法等同于 ANSI c。

- `//` （两个斜杠） 字符后, 跟任何字符序列。 新行不会立即前面有反斜杠终止这种形式的注释。 因此，它通常称为"单行注释"。

注释字符 (`/*`， `*/`，和`//`) 有任何特殊含义，在字符常数，字符串文字，或注释。 因此，不能嵌套使用第一个语法的注释。

## <a name="see-also"></a>请参阅

[词法约定](../cpp/lexical-conventions.md)