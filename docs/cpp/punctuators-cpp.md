---
title: 标点符号 （C++）
ms.date: 11/04/2016
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
ms.openlocfilehash: cef34a17de99a189a590ac3f13c0db9563df643c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478258"
---
# <a name="punctuators-c"></a>标点符号 （C++）

在 C++ 中，标点符号相对于编译器来说具有语法意义和语义含义，但是它们本身不会指定一个产生数值的操作。 某些标点符号（单独或组合）也可以是 C++ 运算符或对预处理器很重要。

以下任意字符都被视为标点符号：

```
! % ^ & * ( ) - + = { } | ~
[ ] \ ; ' : " < > ? , . / #
```

标点符号 **[ ]**，**（ )**，和 **{ }** 必须成对出现在[翻译阶段](../preprocessor/phases-of-translation.md)4。 

## <a name="see-also"></a>请参阅

[词法约定](../cpp/lexical-conventions.md)