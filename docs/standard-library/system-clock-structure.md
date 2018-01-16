---
title: "system_clock 结构 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- chrono/std::chrono::system_clock
- chrono/std::chrono::system_clock::from_time_t
- chrono/std::chrono::system_clock::now
- chrono/std::chrono::system_clock::to_time_t
- chrono/std::chrono::system_clock::is_monotonic Constant
- chrono/std::chrono::system_clock::is_steady Constant
dev_langs: C++
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 603415b438578258e982f0934161d2de436e2a3f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="systemclock-structure"></a>system_clock 结构
表示基于系统实时时钟的*时钟类型*。  
  
## <a name="syntax"></a>语法  
  
```  
struct system_clock;  
```  
  
## <a name="remarks"></a>备注  
 *时钟类型*用于获取作为 UTC 的当前时间。 该类型包含[持续时间](../standard-library/duration-class.md)的实例化和类模板 [time_point](../standard-library/time-point-class.md)，并定义返回时间的静态成员函数 `now()`。  
  
 如果首次调用 `now()` 返回的值始终小于或等于后续调用 `now()` 返回的值，则为单调时钟。  
  
 如果它是单调时钟并且时钟计时周期之间的时间是常量，则为稳定时钟。  
  
 在此实现中，`system_clock` 与 `high_resolution_clock` 是同义词。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`system_clock::duration`|`duration<rep, period>` 的同义词。|  
|`system_clock::period`|该类型的同义词，用于表示在包含的 `duration` 的实例化中的时钟周期。|  
|`system_clock::rep`|该类型的同义词，用于表示在包含的 `duration` 的实例化中的时钟计时周期数。|  
|`system_clock::time_point`|`time_point<Clock, duration>` 的同义词，其中 `Clock` 是时钟类型本身的同义词，或是另一种基于同一时期并具有相同嵌套 `duration` 类型的时钟类型的同义词。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[from_time_t](#from_time_t)|静态。 返回最接近指定的时间的 `time_point`。|  
|[现在](#now)|静态。 返回当前日期。|  
|[to_time_t](#to_time_t)|静态。 返回最接近指定 `time_point` 的 `time_t` 对象。|  
  
### <a name="public-constants"></a>公共常量  
  
|name|描述|  
|----------|-----------------|  
|[system_clock::is_monotonic 常量](#is_monotonic_constant)|指定时钟类型是否为单调。|  
|[system_clock::is_steady 常量](#is_steady_constant)|指定时钟类型是否为稳定。|  
  
## <a name="requirements"></a>惠?  
 **标头：** \<chrono >  
  
 **命名空间：**std::chrono  
  
##  <a name="from_time_t"></a>system_clock:: from_time_t
 返回 [time_point](../standard-library/time-point-class.md) 的静态方法，此返回值最接近 `Tm` 表示的时间。  
  
```  
static time_point from_time_t(time_t Tm) noexcept;  
```  
  
### <a name="parameters"></a>参数  
 `Tm`  
 一个 [time_t](../c-runtime-library/standard-types.md) 对象。  
  
##  <a name="is_monotonic_constant"></a>  system_clock::is_monotonic 常量  
 指定时钟类型是否为单调的静态值。  
  
```  
static const bool is_monotonic = false;  
```  
  
### <a name="return-value"></a>返回值  
 在此实现中，`system_clock::is_monotonic` 始终返回 `false`。  
  
### <a name="remarks"></a>备注  
 如果首次调用 `now()` 返回的值始终小于或等于后续调用 `now()` 返回的值，则为单调时钟。  
  
##  <a name="is_steady_constant"></a>  system_clock::is_steady 常量  
 指定时钟类型是否为*稳定*的静态值。  
  
```  
static const bool is_steady = false;  
```  
  
### <a name="return-value"></a>返回值  
 在此实现中，`system_clock::is_steady` 始终返回 `false`。  
  
### <a name="remarks"></a>备注  
 如果它是[单调](#is_monotonic_constant)时钟并且时钟计时周期之间的时间是常量，则为*稳定*时钟。  
  
##  <a name="now"></a>system_clock:: now
 返回当前时间的静态方法。  
  
```  
static time_point now() noexcept;  
```  
  
### <a name="return-value"></a>返回值  
 表示当前对象的 [time_point](../standard-library/time-point-class.md) 对象。  
  
##  <a name="to_time_t"></a>system_clock:: to_time_t
 返回 [time_t](../c-runtime-library/standard-types.md) 的静态方法，该返回值最接近 `Time` 表示的时间。  
  
```  
static time_t to_time_t(const time_point& Time) noexcept;  
```  
  
### <a name="parameters"></a>参数  
 `Time`  
 一个 [time_point](../standard-library/time-point-class.md) 对象。  
  
## <a name="see-also"></a>请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)   
 [steady_clock 结构](../standard-library/steady-clock-struct.md)
