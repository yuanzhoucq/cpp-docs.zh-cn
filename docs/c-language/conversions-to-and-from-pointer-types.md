---
title: 指针类型之间的转换
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, converting
- conversions, pointer
- type casts, involving pointers
- void pointers
ms.assetid: 3facc56f-06d3-4570-b1a2-7d4927b83086
ms.openlocfilehash: 2d907dbcf4f826d364fb68ce65f7d44c6cfe97cd
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147238"
---
# <a name="conversions-to-and-from-pointer-types"></a>指针类型之间的转换

指向值的一个类型的指针可以转换为指向另一类型的指针。 但是，由于对齐需求和存储中不同类型的大小，结果可能是未定义的。 指向对象的指针可转换为指向其类型要求小于或等于严格存储对齐的对象的指针，然后再次返回而不做更改。

指向 `void` 的指针可转换为/自指向任何类型的指针，且不受限制或不丢失信息。 如果结果转换回原始类型，则将恢复原始指针。

如果指针转换为另一个类型相同但具有不同的或其它限定符的指针，则新指针与旧指针相同（新限定符强加的限制除外）。

指针值也可以转换为整数值。 根据以下规则，转换路径取决于指针的大小和整型的大小：

- 如果指针的大小大于或等于整型的大小，则指针的行为类似于转换中的无符号值，除非它无法转换为浮点值。

- 如果指针小于整型，则指针首先转换为与整型大小相同的指针，然后转换为整型。

相反，整型可以基于以下规则转换为指针类型：

- 如果整型与指针类型的大小相同，则转换只会促使整数值被视为指针（无符号整数）。

- 如果整型类型的大小与指针类型的大小不同，则使用表[从带符号整型类型转换](../c-language/conversions-from-signed-integral-types.md)和[从无符号整型类型转换](../c-language/conversions-from-unsigned-integral-types.md)中给定的转换路径，首先将整型转换为指针的大小。 然后将其视为一个指针值。

带值 0 的整型常量表达式或到类型 void <strong>\*</strong> 的表达式转换可以通过类型转换、赋值或者与指向任何类型的指针进行比较来进行转换。 这将产生与同一类型的另一个 null 指针相等的 null 指针，但此 null 指针与指向函数或对象的任何指针不相等。 常数 0 以外的整数可以转换为指针类型，但结果是不可移植的。

## <a name="see-also"></a>请参阅

[赋值转换](../c-language/assignment-conversions.md)
