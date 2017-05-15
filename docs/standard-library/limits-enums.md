---
title: "&lt;limits&gt; 枚举 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
caps.latest.revision: 11
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 519cc2c696b5dcb67fed79fd04c3e7d66e7d0ad9
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="ltlimitsgt-enums"></a>&lt;limits&gt; 枚举
|||  
|-|-|  
|[float_denorm_style](#float_denorm_style)|[float_round_style](#float_round_style)|  
  
##  <a name="float_denorm_style"></a>float_denorm_style 枚举  
 此枚举描述实现可以选择用于表示非标准化浮点值的各种方法，这种浮点值由于太小而无法表示为规范化值：  
  
```
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```  
  
### <a name="return-value"></a>返回值  
 此枚举返回：  
  
- 如果转换时不能确定是否存在非规范化窗体，则为 **denorm_indeterminate**。  
  
- 如果不存在非规范化窗体，则为 **denorm_absent**。  
  
- 如果存在非规范化窗体，则为 **denorm_present**。  
  
### <a name="example"></a>示例  
  有关可访问此枚举的值的示例，请参阅 [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm)。  
  
##  <a name="float_round_style"></a>float_round_style 枚举  
 此枚举描述实现可以选择用于将浮点值舍入为整数值的各种方法。  
  
```
enum float_round_style {    
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```  
  
### <a name="return-value"></a>返回值  
 此枚举返回：  
  
- 如果无法确定舍入方法，则为 **round_indeterminate**。  
  
- 如果向零舍入，则为 **round_toward_zero**。  
  
- 如果舍入到最近整数，则为 **round_to_nearest**。  
  
- 如果向远离零的方向舍入，则为 **round_toward_infinity**。  
  
- 如果舍入到更小的负整数，则为 **round_toward_neg_infinity**。  
  
### <a name="example"></a>示例  
  有关可访问此枚举的值的示例，请参阅 [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style)。  
  
## <a name="see-also"></a>另请参阅  
 [\<limits>](../standard-library/limits.md)




