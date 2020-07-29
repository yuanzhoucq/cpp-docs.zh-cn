---
title: 迭代语句 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
ms.openlocfilehash: b4176e8265759ae569275bdae5304b0b10c29fc1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227382"
---
# <a name="iteration-statements-c"></a>迭代语句 (C++)

根据一些循环终止条件，迭代语句会导致语句（或复合语句）被执行零次或多次。 当这些语句为复合语句时，它们将按顺序执行，但遇到[break](../cpp/break-statement-cpp.md)语句或[continue](../cpp/continue-statement-cpp.md)语句时除外。

C + + 提供了[四个迭代](../cpp/range-based-for-statement-cpp.md)语句（ [while](../cpp/while-statement-cpp.md)、 [do](../cpp/do-while-statement-cpp.md)、 [for](../cpp/for-statement-cpp.md)和）。 每个迭代都将循环访问，直到其终止表达式的计算结果为零（false），或直到循环终止通过语句强制执行 **`break`** 。 下表汇总了这些语句及其操作；后面各节详细讨论了它们。

### <a name="iteration-statements"></a>迭代语句

|语句|计算位置|初始化|增量|
|---------------|------------------|--------------------|---------------|
|**`while`**|循环的顶部|否|否|
|**`do`**|循环的底部|否|否|
|**`for`**|循环的顶部|是|是|
|**range-based for**|循环的顶部|是|是|

迭代语句的语句部分不能为声明。 但是，它可以是包含声明的复合语句。

## <a name="see-also"></a>另请参阅

[C + + 语句概述](../cpp/overview-of-cpp-statements.md)
