---
title: completion_future 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- completion_future
- AMPRT/completion_future
- AMPRT/Concurrency::completion_future::completion_future
- AMPRT/Concurrency::completion_future::get
- AMPRT/Concurrency::completion_future::then
- AMPRT/Concurrency::completion_future::to_task
- AMPRT/Concurrency::completion_future::valid
- AMPRT/Concurrency::completion_future::wait
- AMPRT/Concurrency::completion_future::wait_for
- AMPRT/Concurrency::completion_future::wait_until
dev_langs:
- C++
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 835c3a0473ffc68a2b1e32780fc2eb376f0ceee6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118125"
---
# <a name="completionfuture-class"></a>completion_future 类
表示一个未来，对应于 c + + AMP 的异步操作。  
  
### <a name="syntax"></a>语法  
  
```  
class completion_future;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[completion_future 构造函数](#ctor)|初始化 `completion_future` 类的新实例。|  
|[~ completion_future 析构函数](#dtor)|销毁`completion_future`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[get](#get)|等待，直到关联的异步操作完成。|  
|[then](#then)|链接到一个回调函数对象`completion_future`关联的异步操作完成执行时要执行对象。|  
|[to_task](#to_task)|返回`task`对应于关联的异步操作对象。|  
|[valid](#valid)|获取一个布尔值，该值指示对象是否与异步操作相关联。|  
|[等待](#wait)|阻止，直到关联的异步操作完成。|  
|[wait_for](#wait_for)|阻止，直到关联的异步操作完成或由指定的时间`_Rel_time`已过。|  
|[wait_until](#wait_until)|阻止，直到关联的异步操作完成或当前时间超过指定的值直到`_Abs_time`。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator std::shared_future\<void>](#operator_shared_future)|将隐式转换`completion_future`对象传递给`std::shared_future`对象。|  
|[operator=](#operator_eq)|将指定的内容复制`completion_future`到此对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `completion_future`  
  
## <a name="requirements"></a>要求  
 **标头：** amprt.h  
  
 **命名空间：** 并发  


## <a name="ctor"></a> completion_future 

初始化 `completion_future` 类的新实例。  
  
### <a name="syntax"></a>语法  
  
```  
completion_future();  
  
completion_future(  
    const completion_future& _Other );  
  
completion_future(  
    completion_future&& _Other );  
```  
  
### <a name="parameters"></a>参数  
*_Other*<br/>
要复制或移动的 `completion_future` 对象。  
  
### <a name="overloads-list"></a>重载列表  
  
|name|描述|  
|----------|-----------------|  
|`completion_future();`|初始化 `completion_future` 类的新实例。|  
|`completion_future(const completion_future& _Other);`|通过复制构造函数来初始化 `completion_future` 类的新实例。|  
|`completion_future(completion_future&& _Other);`|通过移动构造函数来初始化 `completion_future` 类的新实例。|  
  
## <a name="get"></a> 获取 

等待，直到关联的异步操作完成。 如果在异步操作时遇到存储的异常，则将引发该异常。  
  
### <a name="syntax"></a>语法  
  
```  
void get() const;  
```  
  
## <a name="operator_shared_future"></a> operator std::shared_future<void> 

将隐式转换`completion_future`对象传递给`std::shared_future`对象。  
  
### <a name="syntax"></a>语法  
  
```  
operator std::shared_future<void>() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个 `std::shared_future` 对象。  
  
## <a name="operator_eq"></a> 运算符 = 

将指定的内容复制`completion_future`到此对象。  
  
### <a name="syntax"></a>语法  
  
```  
completion_future&  operator= (const completion_future& _Other );    
completion_future&  operator= (completion_future&& _Other );  
```  
  
### <a name="parameters"></a>参数  
*_Other*<br/>
从其中复制的对象。  
  
### <a name="return-value"></a>返回值  
 对此引用`completion_future`对象。  
  
## <a name="overloads-list"></a>重载列表  
  
|name|描述|  
|----------|-----------------|  
|`completion_future& operator=(const completion_future& _Other);`|使用深层复制将指定 `completion_future` 对象的内容复制到此对象中。|  
|`completion_future& operator=(completion_future&& _Other);`|使用移动赋值将指定 `completion_future` 对象的内容复制到此对象中。|  
  
## <a name="then"></a> 然后 

链接到一个回调函数对象`completion_future`关联的异步操作完成执行时要执行对象。  
  
### <a name="syntax"></a>语法  
  
```  
template <typename _Functor>  
void then(const _Functor & _Func ) const;  
```  
  
### <a name="parameters"></a>参数  
*_Functor*<br/>
回调函子。  
  
*_Func*<br/>
回调函数对象。  
  
## <a name="to_task"></a> to_task 

返回`task`对应于关联的异步操作对象。  
  
### <a name="syntax"></a>语法  
  
```  
concurrency::task<void> to_task() const;  
```  
  
### <a name="return-value"></a>返回值  
 对应于关联的异步操作的 `task` 对象。  
  
## <a name="valid"></a> 有效 

获取一个布尔值，指示该对象是否与异步操作关联。  
  
### <a name="syntax"></a>语法  
  
```  
bool valid() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果该对象与异步操作关联，则为 `true`；否则为 `false`。  
  
## <a name="wait"></a> 等待 

阻止，直到关联的异步操作完成。  
  
### <a name="syntax"></a>语法  
  
```  
void wait() const;  
```  
  
## <a name="wait_for"></a> wait_for 

阻止，直到关联的异步操作完成或由指定的时间`_Rel_time`已过。  
  
### <a name="syntax"></a>语法  
  
```  
template <  
    class _Rep,  
    class _Period  
>  
std::future_status::future_status wait_for(  
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;  
```  
  
### <a name="parameters"></a>参数  
*_Rep*<br/>
算术类型表示的计时周期数。  
  
*_Period*<br/>
Std::ratio，它表示每个滴答等待的秒数。  
  
*_Rel_time*<br/>
最长时间等待操作完成。  
  
### <a name="return-value"></a>返回值  
 返回：  
  
-   `std::future_status::deferred` 如果未运行关联的异步操作。  
  
-   `std::future_status::ready` 如果关联的异步操作已完成。  
  
-   `std::future_status::timeout` 如果指定时间段内已过。  
  
## <a name="wait_until"></a> wait_until 

阻止，直到关联的异步操作完成或当前时间超过指定的值直到`_Abs_time`。  
  
### <a name="syntax"></a>语法  
  
```  
template <  
    class _Clock,  
    class _Duration  
>  
std::future_status::future_status wait_until(  
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;  
```  
  
### <a name="parameters"></a>参数  
*_Clock*<br/>
此时间点测量的时钟。  
  
*_Duration*<br/>
自启动以来的时间间隔`_Clock`的时期，此后该函数将超时时间。  
  
*_Abs_time*<br/>
此后该函数将超时的时间点。  
  
### <a name="return-value"></a>返回值  
 返回：  
  
1.  `std::future_status::deferred` 如果未运行关联的异步操作。  
  
2.  `std::future_status::ready` 如果关联的异步操作已完成。  
  
3.  `std::future_status::timeout` 如果指定的时间段已过。  
  
## <a name="dtor"></a> ~ completion_future 

销毁`completion_future`对象。  
  
### <a name="syntax"></a>语法  
  
```  
~completion_future();  
```  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
