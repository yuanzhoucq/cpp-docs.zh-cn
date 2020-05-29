---
title: 标点符号 （C++）
ms.date: 11/04/2016
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
ms.openlocfilehash: cc4e56cd0dce3ae91183a8675eba96f174c3c31f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160966"
---
# <a name="punctuators-c"></a>标点符号 （C++）

在 C++ 中，标点符号相对于编译器来说具有语法意义和语义含义，但是它们本身不会指定一个产生数值的操作。 某些标点符号（单独或组合）也可以是 C++ 运算符或对预处理器很重要。

以下任意字符都被视为标点符号：

```
! % ^ & * ( ) - + = { } | ~
[ ] \ ; ' : " < > ? , . / #
```

[翻译阶段](../preprocessor/phases-of-translation.md)4 后，标点符号 **[]** 、 **（）** 和 **{}** 必须成对出现。

## <a name="see-also"></a>另请参阅

[词法约定](../cpp/lexical-conventions.md)
