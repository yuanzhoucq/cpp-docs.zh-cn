---
title: 聚合和联合 |Microsoft 文档
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
ms.openlocfilehash: 5b1afd3be89e1d18da9889d88dbbbef3fb104e02
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363254"
---
# <a name="aggregates-and-unions"></a>聚合和联合
其他类型，如数组、 结构和联合，具有更严格的对齐要求，以确保一致聚合和联合存储和数据检索。 下面是数组、 结构和联合的定义：  
  
 数组  
 包含相邻的数据对象的有序的组。 每个对象称为一个元素。 在数组内的所有元素都具有相同的大小和数据类型。  
  
 结构  
 包含数据对象的有序的组。 与数组的元素，不同结构中的数据对象可以具有不同的数据类型和大小。 结构中的每个数据对象称为成员。  
  
 联合  
 包含一组命名的任何的成员一个对象。 命名集的成员可以是任何类型。 对于联合分配的存储等于该联合，加上对齐所需的任何填充的最大成员所需的存储。  
  
 下表显示联合和结构的标量成员的强烈建议对齐方式。  
  
||||  
|-|-|-|  
|标量类型|C 数据类型|所需的对齐方式|  
|**INT8**|`char`|Byte|  
|**UINT8**|`unsigned char`|Byte|  
|**INT16**|**short**|字|  
|**UINT16**|**unsigned short**|字|  
|**INT32**|**int、 long**|双字|  
|**UINT32**|**无符号长的无符号的整数**|双字|  
|**INT64**|`__int64`|四字|  
|**UINT64**|unsigned __int64|四字|  
|**FP32 （单精度）**|**float**|双字|  
|**FP64 （双精度）**|**double**|四字|  
|**指针**|**\***|四字|  
|`__m64`|**结构 __m64**|四字|  
|`__m128`|**结构 __m128**|Octaword|  
  
 适用以下聚合对齐规则：  
  
-   数组的对齐方式是一个数组的元素的对齐方式相同。  
  
-   一个结构或联合的对齐方式是开头的任何单个成员的最大对齐方式。 在结构或联合中的每个成员必须位于其正确对齐上, 表中，这可能需要隐式的内部填充，具体取决于上一个成员中定义。  
  
-   结构大小必须为自己的对齐方式，这可能需要后的最后一个成员的填充的整数倍。 由于结构和联合可在数组中进行分组，结构或联合的每个数组元素必须开始和结束在先前确定的正确对齐方式。  
  
-   很可能将数据，只要保留以前的规则可大于对齐需求的方式对齐。  
  
-   单个编译器可能会调整大小原因结构的包装。 例如[/Zp （结构成员对齐）](../build/reference/zp-struct-member-alignment.md)允许调整结构的包装。  
  
## <a name="see-also"></a>请参阅  
 [类型和存储](../build/types-and-storage.md)
