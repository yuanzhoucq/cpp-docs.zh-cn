---
title: "duration_values 结构 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
dev_langs:
- C++
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 996e0b02ade2f6c88c1f46ee9f84bbb28cfffdd7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
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
  
|名称|描述|  
|----------|-----------------|  
|[max](#max)|静态。 指定类型 `Rep` 的值上限。|  
|[min](#min)|静态。 指定类型 `Rep` 的值下限。|  
|[zero](#zero)|静态。 返回 `Rep(0)`。|  
  
## <a name="requirements"></a>惠?  
 **标头：** \<chrono >  
  
 **命名空间：**std::chrono  
  
##  <a name="max"></a>  duration_values::max  
 返回类型 `Ref` 的值上限的静态方法。  
  
```  
static constexpr Rep max();
```  
  
### <a name="return-value"></a>返回值  
 实际上，返回 `numeric_limits<Rep>::max()`。  
  
### <a name="remarks"></a>备注  
 当 `Rep` 是用户定义类型时，返回值必须大于 [duration_values::zero](#zero)。  
  
##  <a name="min"></a>  duration_values::min  
 返回类型值下限的静态方法`Ref`。  
  
```  
static constexpr Rep min();
```  
  
### <a name="return-value"></a>返回值  
 实际上，返回 `numeric_limits<Rep>::lowest()`。  
  
### <a name="remarks"></a>备注  
 当 `Rep` 是用户定义类型时，返回值必须小于或等于 [duration_values::zero](#zero)。  
  
##  <a name="zero"></a>  duration_values::zero  
 返回 `Rep(0)`。  
  
```  
static constexpr Rep zero();
```  
  
### <a name="remarks"></a>备注  
 当 `Rep` 是用户定义类型时，返回值必须表示正无穷大。  
  
## <a name="see-also"></a>请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)

