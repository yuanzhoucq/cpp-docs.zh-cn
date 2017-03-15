---
title: "&lt;limits&gt; 枚举 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: e0f4b6ca5d11207787f9ff4f27b21dbbc78080c0
ms.lasthandoff: 02/24/2017

---
# <a name="ltlimitsgt-enums"></a>&lt;limits&gt; 枚举
|||  
|-|-|  
|[float_denorm_style 枚举](#float_denorm_style_enumeration)|[float_round_style 枚举](#float_round_style_enumeration)|  
  
##  <a name="a-namefloatdenormstyleenumerationa--floatdenormstyle-enumeration"></a><a name="float_denorm_style_enumeration"></a>float_denorm_style 枚举  
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
  有关可访问此枚举的值的示例，请参阅 [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#numeric_limits__has_denorm)。  
  
##  <a name="a-namefloatroundstyleenumerationa--floatroundstyle-enumeration"></a><a name="float_round_style_enumeration"></a>float_round_style 枚举  
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
  有关可访问此枚举的值的示例，请参阅 [numeric_limits::round_style](../standard-library/numeric-limits-class.md#numeric_limits__round_style)。  
  
## <a name="see-also"></a>另请参阅  
 [\<limits>](../standard-library/limits.md)




