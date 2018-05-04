---
title: 标量类型 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 07c9195e-b6c7-4083-8ef0-8a93032e4d1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5490bb33cafd8d2942e434ab9c50e34441506463
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="scalar-types"></a>标量类型
虽然数据的访问可能源于任何的对齐方式，建议，在以避免性能损失 （或更多损失） 其自然边界上对齐数据。 枚举是常量的整数，而是被视为 32 位整数。 下表描述的类型定义和建议的存储为其与使用以下的对齐方式值的对齐方式：  
  
-   字节的 8 位  
  
-   Word 的 16 位  
  
-   双字的 32 位  
  
-   四 Word-64 位  
  
-   Octa Word-128 位  
  
|||||  
|-|-|-|-|  
|标量类型|C 数据类型|存储大小 （以字节为单位）|建议的对齐方式|  
|**INT8**|`char`|1|Byte|  
|**UINT8**|`unsigned char`|1|Byte|  
|**INT16**|**short**|2|字|  
|**UINT16**|**unsigned short**|2|字|  
|**INT32**|**int、 long**|4|双字|  
|**UINT32**|**无符号长的无符号的整数**|4|双字|  
|**INT64**|`__int64`|8|四字|  
|**UINT64**|unsigned __int64|8|四字|  
|**FP32 （单精度）**|**float**|4|双字|  
|**FP64 （双精度）**|**double**|8|四字|  
|**指针**|**\***|8|四字|  
|`__m64`|**结构 __m64**|8|四字|  
|`__m128`|**结构 __m128**|16|Octaword|  
  
## <a name="see-also"></a>请参阅  
 [类型和存储](../build/types-and-storage.md)