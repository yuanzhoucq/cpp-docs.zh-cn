---
title: "&lt;thread&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
caps.latest.revision: 12
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: de302b9a2d971b2a39d4ce775799f27dd7244a5c
ms.lasthandoff: 02/24/2017

---
# <a name="ltthreadgt-functions"></a>&lt;thread&gt; 函数
||||  
|-|-|-|  
|[get_id](#get_id_function)|[sleep_for](#sleep_for_function)|[sleep_until](#sleep_until_function)|  
|[swap](#swap_function)|[yield](#yield_function)|  
  
##  <a name="a-namegetidfunctiona--getid"></a><a name="get_id_function"></a>  get_id  
 唯一标识当前的执行线程。  
  
```  
thread::id this_thread::get_id() noexcept;  
```  
  
### <a name="return-value"></a>返回值  
 类型为 [thread:: id](../standard-library/thread-class.md) 的对象，用于唯一标识当前的执行线程。  
  
##  <a name="a-namesleepforfunctiona--sleepfor"></a><a name="sleep_for_function"></a>  sleep_for  
 阻止调用线程。  
  
```  
template <class Rep,  
class Period>  
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```  
  
### <a name="parameters"></a>参数  
 `Rel_time`  
 用于指定时间间隔的 [duration](../standard-library/duration-class.md) 对象。  
  
### <a name="remarks"></a>备注  
 该函数在一定时间内阻止调用线程，时间至少是由 `Rel_time` 指定的时间。 此函数不引发任何异常。  
  
##  <a name="a-namesleepuntilfunctiona--sleepuntil"></a><a name="sleep_until_function"></a>  sleep_until  
 阻止调用线程，至少直到指定的时间。  
  
```  
template <class Clock, class Duration>  
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```  
  
### <a name="parameters"></a>参数  
 `Abs_time`  
 表示时间点。  
  
### <a name="remarks"></a>备注  
 此函数不引发任何异常。  
  
##  <a name="a-nameswapfunctiona--swap"></a><a name="swap_function"></a>swap  
 交换两个 `thread` 对象的状态。  
  
```  
void swap(thread& Left, thread& Right) noexcept;  
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左 `thread` 对象。  
  
 `Right`  
 正确的 `thread` 对象。  
  
### <a name="remarks"></a>备注  
 函数调用 `Left.swap(Right)`。  
  
##  <a name="a-nameyieldfunctiona--yield"></a><a name="yield_function"></a>  yield  
 表示要运行其他线程的操作系统，即使当前线程会照常继续运行。  
  
```  
inline void yield() noexcept;  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<thread>](../standard-library/thread.md)


