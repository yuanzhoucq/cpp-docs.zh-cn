---
title: 加 (+)
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, adding integers
ms.assetid: b9014fee-825d-46ef-91db-5d46807081fc
ms.openlocfilehash: 48672315960e32cb324aacc6c90d3d67891f3d39
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149877"
---
# <a name="addition-"></a>加 (+)

加法运算符 (+) 导致添加其两个操作数。 两个操作数可同时为整型或浮点型，或者一个操作数为指针，另一个操作数为整数。

在将整数添加到指针时，会通过将整数值 (i) 乘以指针寻址的值的大小来转换该整数值。 转换后，整数值表示 *i* 个内存位置，其中每个位置均具有指针类型所指定的长度。 在将转换的整数值添加到指针值时，结果为表示原始地址中的地址 i 位置的新指针值。 新指针值对类型与原始指针值的类型相同的值进行寻址，因此它与数组索引相同（请参阅[一维数组](../c-language/one-dimensional-arrays.md)和[多维数组](../c-language/multidimensional-arrays-c.md)）。 如果 sum 指针指向数组的外部，除非位于在高端外的第一个位置，否则结果是不确定的。 有关详细信息，请参阅[指针算法](../c-language/pointer-arithmetic.md)。

## <a name="see-also"></a>请参阅

[C 加法运算符](../c-language/c-additive-operators.md)
