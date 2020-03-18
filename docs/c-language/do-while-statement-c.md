---
title: do-while 语句 (C)
ms.date: 11/04/2016
f1_keywords:
- do
helpviewer_keywords:
- do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
ms.openlocfilehash: 3658fe7635ad77db6d6e08ff9d7c30e29d665721
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438587"
---
# <a name="do-while-statement-c"></a>do-while 语句 (C)

利用 do-while 语句，可以重复语句或复合语句，直到指定的表达式的计算结果为 false。

## <a name="syntax"></a>语法

*迭代语句*： &nbsp;&nbsp;&nbsp;**在（** *expression* **）** 时 &nbsp;**do***语句*;

在执行循环体后，将计算 do-while 语句中的 expression。 因此，总是至少执行一次循环体。

expression必须具有算法或指针类型。 执行过程如下所示：

1. 执行语句体。

1. 接着，计算 expression。 如果 expression 为 false，则 do-while 语句将终止，控制权将传递到程序中的下一条语句。 如果 expression 为 true（非零），则将从第 1 步开始重复此过程。

do-while 语句还可在语句体中执行 break、goto 或 return 语句时终止。

以下是 do-while 语句的示例：

```C
do
{
    y = f( x );
    x--;
} while ( x > 0 );
```

在此 do-while 语句中，无论 `y = f( x );` 的初始值是什么，`x--;` 和 `x` 这两个语句都会执行。 然后将计算 `x > 0`。 如果 `x` 大于 0，则会再次执行语句体并重新计算 `x > 0`。 只要 `x` 保持大于 0，语句主体就会重复执行。 当  *变为 0 或负值时，do-while*`x` 语句的执行将终止。 将至少执行一次循环体。

## <a name="see-also"></a>另请参阅

[do-while 语句 (C++)](../cpp/do-while-statement-cpp.md)
