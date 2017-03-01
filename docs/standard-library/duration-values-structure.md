---
title: "duration_values 结构 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- chrono/std::chrono::duration_values
dev_langs:
- C++
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 8b0c02d4edc3a460f166cb65b312ef78337d403f
ms.lasthandoff: 02/24/2017

---
# <a name="durationvalues-structure"></a>duration_values 结构
为[持续时间](../standard-library/duration-class.md)模板参数 `Rep` 提供指定值。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Rep>  
struct duration_values;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[duration_values::max](#duration_values__max_method)|静态。 指定类型 `Rep` 的值上限。|  
|[duration_values::min](#duration_values__min_method)|静态。 指定类型 `Rep` 的值下限。|  
|[duration_values::zero](#duration_values__zero_method)|静态。 返回 `Rep(0)`。|  
  
## <a name="requirements"></a>要求  
 **标头：**chrono  
  
 **命名空间：**std::chrono  
  
##  <a name="a-namedurationvaluesmaxmethoda--durationvaluesmax"></a><a name="duration_values__max_method"></a>  duration_values::max  
 返回类型 `Ref` 的值上限的静态方法。  
  
```  
static constexpr Rep max();
```  
  
### <a name="return-value"></a>返回值  
 实际上，返回 `numeric_limits<Rep>::max()`。  
  
### <a name="remarks"></a>备注  
 当 `Rep` 是用户定义类型时，返回值必须大于 [duration_values::zero](#duration_values__zero_method)。  
  
##  <a name="a-namedurationvaluesminmethoda--durationvaluesmin"></a><a name="duration_values__min_method"></a>  duration_values::min  
 返回类型值下限的静态方法`Ref`。  
  
```  
static constexpr Rep min();
```  
  
### <a name="return-value"></a>返回值  
 实际上，返回 `numeric_limits<Rep>::lowest()`。  
  
### <a name="remarks"></a>备注  
 当 `Rep` 是用户定义类型时，返回值必须小于或等于 [duration_values::zero](#duration_values__zero_method)。  
  
##  <a name="a-namedurationvalueszeromethoda--durationvalueszero"></a><a name="duration_values__zero_method"></a>  duration_values::zero  
 返回 `Rep(0)`。  
  
```  
static constexpr Rep zero();
```  
  
### <a name="remarks"></a>备注  
 当 `Rep` 是用户定义类型时，返回值必须表示正无穷大。  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)


