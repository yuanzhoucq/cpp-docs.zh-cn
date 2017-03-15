---
title: "future 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::future
dev_langs:
- C++
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 6de4fecd3f5f65ac48cbb49f2ed4f874f4283487
ms.lasthandoff: 02/24/2017

---
# <a name="future-class"></a>future 类
描述异步返回对象。  
  
## <a name="syntax"></a>语法  
  
```
template <class Ty>
class future;
```  
  
## <a name="remarks"></a>备注  
 每个标准*异步提供程序*返回一个对象，该对象的类型是此模板的实例化。 `future` 对象提供与其关联的异步提供程序的唯一访问权限。 如需多个与同一异步提供程序关联的异步返回对象，请将 `future` 对象复制到 [shared_future](../standard-library/shared-future-class.md) 对象。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[future::future Constructor](#future__future_constructor)|构造 `future` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[future::get](#future__get_method)|检索存储在关联异步状态中的结果。|  
|[future::share](#future__share_method)|将对象转换为 `shared_future`。|  
|[future::valid](#future__valid_method)|指定对象是否不为空。|  
|[future::wait](#future__wait_method)|阻止当前线程，直到关联异步状态为准备就绪。|  
|[future::wait_for](#future__wait_for_method)|进行阻止，直到关联异步状态为准备就绪或已过指定时间。|  
|[future::wait_until](#future__wait_until_method)|进行阻止，直到关联异步状态为准备就绪或直到指定时间点。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[future::operator=](#future__operator_eq)|从指定对象传输关联异步状态。|  
  
## <a name="requirements"></a>要求  
 **标头：**future  
  
 **命名空间：** std  
  
##  <a name="a-namefuturefutureconstructora--futurefuture-constructor"></a><a name="future__future_constructor"></a>future::future 构造函数  
 构造 `future` 对象。  
  
```
future() noexcept;
future(future&& Other) noexcept;
```  
  
### <a name="parameters"></a>参数  
 `Other`  
 一个 `future` 对象。  
  
### <a name="remarks"></a>备注  
 第一个构造函数构造没有关联异步状态的 `future` 对象。  
  
 第二个构造函数构造 `future` 对象并从 `Other` 传输关联异步状态。 `Other` 不再具有关联异步状态。  
  
##  <a name="a-namefuturegetmethoda--futureget"></a><a name="future__get_method"></a>future::get  
 检索存储在关联异步状态中的结果。  
  
```
Ty get();
```  
  
### <a name="return-value"></a>返回值  
 如果结果为异常，该方法将重新引发它。 否则，会返回结果。  
  
### <a name="remarks"></a>备注  
 在检索结果前，该方法会阻止当前线程，直到关联异步状态为准备就绪。  
  
 对于部分专用化 `future<Ty&>`，存储值实际上是对已传递给异步提供程序作为返回值的对象的引用。  
  
 因为专用化 `future<void>` 不存在任何存储值，所以此方法会返回 `void`。  
  
 在其他专用化中，此方法会从存储值移动其返回值。 因此，请仅调用此方法一次。  
  
##  <a name="a-namefutureoperatoreqa--futureoperator"></a><a name="future__operator_eq"></a>future::operator=  
 从指定对象传输关联异步状态。  
  
```
future& operator=(future&& Right) noexcept;
```  
  
### <a name="parameters"></a>参数  
 `Right`  
 一个 `future` 对象。  
  
### <a name="return-value"></a>返回值  
 `*this`  
  
### <a name="remarks"></a>备注  
 传输后，`Right` 不再具有关联异步状态。  
  
##  <a name="a-namefuturesharemethoda--futureshare"></a><a name="future__share_method"></a>future::share  
 将对象转换为 [shared_future](../standard-library/shared-future-class.md) 对象。  
  
```
shared_future<Ty> share();
```  
  
### <a name="return-value"></a>返回值  
 `shared_future(move(*this))`  
  
##  <a name="a-namefuturevalidmethoda--futurevalid"></a><a name="future__valid_method"></a>future::valid  
 指定对象是否具有关联异步状态。  
  
```
bool valid() noexcept;
```  
  
### <a name="return-value"></a>返回值  
 如果对象有关联的异步状态，则为 `true`；否则为 `false`。  
  
##  <a name="a-namefuturewaitmethoda--futurewait"></a><a name="future__wait_method"></a>future::wait  
 阻止当前线程，直到关联异步状态为准备就绪。  
  
```cpp  
void wait() const;
```  
  
### <a name="remarks"></a>备注  
 只有当其异步提供程序存储了返回值或存储了异常时，关联的异步状态才会为准备就绪。  
  
##  <a name="a-namefuturewaitformethoda--futurewaitfor"></a><a name="future__wait_for_method"></a>future::wait_for  
 阻止当前线程，直到关联异步状态为准备就绪或已过指定时间间隔。  
  
```
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```  
  
### <a name="parameters"></a>参数  
 `Rel_time`  
 一个 [chrono::duration](../standard-library/duration-class.md) 对象，指定线程阻止的最大时间间隔。  
  
### <a name="return-value"></a>返回值  
 一个 [future_status](../standard-library/future-enums.md#future_status_enumeration)，指示返回的原因。  
  
### <a name="remarks"></a>备注  
 只有当其异步提供程序存储了返回值或存储了异常时，关联的异步状态才会为准备就绪。  
  
##  <a name="a-namefuturewaituntilmethoda--futurewaituntil"></a><a name="future__wait_until_method"></a>future::wait_until  
 阻止当前线程，直到关联的异步状态为准备就绪或直到指定时间点后。  
  
```cpp  
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```  
  
### <a name="parameters"></a>参数  
 `Abs_time`  
 一个 [chrono::time_point](../standard-library/time-point-class.md) 对象，指定在其后可取消阻止线程的时间。  
  
### <a name="return-value"></a>返回值  
 一个 [future_status](../standard-library/future-enums.md#future_status_enumeration)，指示返回的原因。  
  
### <a name="remarks"></a>备注  
 只有当其异步提供程序存储了返回值或存储了异常时，关联的异步状态才会为准备就绪。  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<future>](../standard-library/future.md)




