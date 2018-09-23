---
title: 简单赋值 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff4e032e205680da84369075514e3177fa5fb33e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051017"
---
# <a name="simple-assignment-c"></a>简单赋值 (C)

简单赋值运算符可将其右操作数赋给其左操作数。 右操作数的值将转换为赋值表达式的类型，并替换存储在左侧操作数指定的对象中的值。 用于赋值的转换规则适用（请参阅[赋值转换](../c-language/assignment-conversions.md)）。

```
double x;
int y;

x = y;
```

在此示例中，将 `y` 的值转换为类型 double 并赋给 `x`。

## <a name="see-also"></a>请参阅

[C 赋值运算符](../c-language/c-assignment-operators.md)