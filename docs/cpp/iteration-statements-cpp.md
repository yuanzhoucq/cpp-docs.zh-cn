---
title: 迭代语句 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
ms.openlocfilehash: 72f81e2fc58a31db0c4cd3f77ba182bd8b8152a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366571"
---
# <a name="iteration-statements-c"></a>迭代语句 (C++)

根据一些循环终止条件，迭代语句会导致语句（或复合语句）被执行零次或多次。 当这些语句是复合语句时，它们的顺序执行，除非任一[中断](../cpp/break-statement-cpp.md)语句或[继续](../cpp/continue-statement-cpp.md)遇到语句。

C++ 提供四个迭代语句-[while](../cpp/while-statement-cpp.md)，[do](../cpp/do-while-statement-cpp.md)，[for](../cpp/for-statement-cpp.md)，和[基于范围的 for](../cpp/range-based-for-statement-cpp.md)。 每个迭代，直到其终止表达式的计算结果为零 (false)，或使用强制循环终止**中断**语句。 下表汇总了这些语句及其操作；后面各节详细讨论了它们。

### <a name="iteration-statements"></a>迭代语句

|语句|计算位置|初始化|递增|
|---------------|------------------|--------------------|---------------|
|**while**|循环的顶部|否|否|
|**do**|循环的底部|否|否|
|**for**|循环的顶部|是|是|
|**基于范围的 for**|循环的顶部|是|是|

迭代语句的语句部分不能为声明。 但是，它可以是包含声明的复合语句。

## <a name="see-also"></a>请参阅

[ 语句概述](../cpp/overview-of-cpp-statements.md)
