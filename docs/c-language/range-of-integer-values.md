---
title: 整数值的范围 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 0e9c6161-8f3f-4bfb-9fcc-a6c8dc97d702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2695b5d2a006529042453b7048bec400388fb74b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="range-of-integer-values"></a>整数值的范围
**ANSI 3.1.2.5**：各种类型的整数值的表示形式和集  
  
 整数包含 32 位（4 个字节）。 带符号整数以 2 的补数的形式表示。 最高有效位保存符号：1 表示负数，0 表示整数或零。 下面列出了这些值：  
  
|类型|最小值和最大值|  
|----------|-------------------------|  
|**unsigned short**|0 到 65535|  
|`signed short`|-32768 到 32767|  
|`unsigned long`|0 到 4294967295|  
|**signed long**|-2147483648 到 2147483647|  
  
## <a name="see-also"></a>请参阅  
 [整数](../c-language/integers.md)