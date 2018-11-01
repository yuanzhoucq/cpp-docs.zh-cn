---
title: 表达式语句
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
ms.openlocfilehash: 2973c3e0a1cd59edfc7ef1e771454b780da23cf9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562443"
---
# <a name="expression-statement"></a>表达式语句

表达式语句导致计算表达式。 出于表达式语句的原因，不会发生控制或迭代的传输。

表达式语句的语法就是

## <a name="syntax"></a>语法

```
[expression ] ;
```

## <a name="remarks"></a>备注

在执行下一个语句前，将计算表达式语句中的所有表达式并完成所有副作用。 最常用的表达式语句是赋值和函数调用。  由于表达式是可选的因此单独的分号被视为空表达式语句，称为[null](../cpp/null-statement.md)语句。

## <a name="see-also"></a>请参阅

[ 语句概述](../cpp/overview-of-cpp-statements.md)