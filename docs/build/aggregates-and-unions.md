---
title: 聚合和联合 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregates [C++], and unions
ms.assetid: 859fc211-b111-4f12-af98-de78e48f9b92
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aac6da94a0786e5cdc2eee4d16f5927f66e0a8d5
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861182"
---
# <a name="aggregates-and-unions"></a>聚合和联合

其他类型，如数组、 结构和联合，具有更严格对齐要求，以确保一致聚合和联合存储和数据检索。 下面是数组、 结构和联合的定义：

- 数组

   包含相邻的数据对象的有序的组。 每个对象调用一个元素。 一个数组中的所有元素都具有相同的大小和数据类型。

- 结构

   包含数据对象的有序的组。 与数组的元素，在结构中的数据对象可以具有不同的数据类型和大小。 在结构中的每个数据对象调用成员。

- 联合

   保存一组命名的成员之一的对象。 命名集的成员可以是任何类型。 分配为联合的存储等于该联合，加上任何填充所需的对齐方式的最大成员所需的存储。

下表显示了标量联合和结构的成员的强烈建议对齐方式。

||||
|-|-|-|
|标量类型|C 数据类型|所需的对齐方式|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|字|
|**UINT16**|**unsigned short**|字|
|**INT32**|**int**，**长**|双字|
|**UINT32**|**无符号的整型、 无符号长**|双字|
|**INT64**|**__int64**|四字|
|**UINT64**|unsigned __int64|四字|
|**FP32 （单精度）**|**float**|双字|
|**FP64 （双精度）**|**double**|四字|
|**指针**|<strong>\*</strong>|四字|
|**__m64**|**结构 __m64**|四字|
|**__m128**|**结构 __m128**|Octaword|

以下聚合对齐规则适用：

- 数组的对齐方式是一个数组的元素的对齐方式相同。

- 开始处的结构或联合的对齐方式为任何单个成员的最大对齐方式。 结构或联合中的每个成员必须位于其正确对齐上, 表中，这可能需要隐式内部的填充量，具体取决于上一个成员中定义。

- 结构大小必须为其对齐方式，可能需要填充的最后一个成员后的整数倍。 由于结构和联合可以分组在数组中，结构或联合的每个数组元素必须开始和结束处先前确定的适当对齐方式。

- 就可以保持一致的方式将其大于对齐要求，只要将保留以前的规则中的数据。

- 单个编译器可能会调整大小的原因的结构的包装。 例如[/Zp （结构成员对齐）](../build/reference/zp-struct-member-alignment.md)允许进行调整的结构的包装。

## <a name="see-also"></a>请参阅

[类型和存储](../build/types-and-storage.md)
