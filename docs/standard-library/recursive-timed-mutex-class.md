---
title: "recursive_timed_mutex 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::recursive_timed_mutex
dev_langs:
- C++
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
caps.latest.revision: 9
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: a28e9521455f0380f412fc2aa81aecd713f9535a
ms.lasthandoff: 02/24/2017

---
# <a name="recursivetimedmutex-class"></a>recursive_timed_mutex 类
表示定时互斥体类型。 此类型的对象用于在程序内通过使用时间限制阻止来强制实现互相排斥。 与 [timed_mutex](../standard-library/timed-mutex-class.md) 类型的对象不同，为 `recursive_timed_mutex` 对象调用锁定方法的效果是有明确定义的。  
  
## <a name="syntax"></a>语法  
  
```
class recursive_timed_mutex;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[recursive_timed_mutex 构造函数](#recursive_timed_mutex__recursive_timed_mutex_constructor)|构造未锁定的 `recursive_timed_mutex` 对象。|  
|[~recursive_timed_mutex 析构函数](#recursive_timed_mutex___dtorrecursive_timed_mutex_destructor)|释放由 `recursive_timed_mutex` 对象使用的任何资源。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[lock](#recursive_timed_mutex__lock_method)|阻止调用线程，直到线程获取 `mutex` 的所有权。|  
|[try_lock](#recursive_timed_mutex__try_lock_method)|在不阻止的情况下尝试获取 `mutex` 的所有权。|  
|[try_lock_for](#recursive_timed_mutex__try_lock_for_method)|尝试获取在指定时间间隔内有效的 `mutex` 的所有权。|  
|[try_lock_until](#recursive_timed_mutex__try_lock_until_method)|尝试获取在指定时间之前有效的 `mutex` 的所有权。|  
|[unlock](#recursive_timed_mutex__unlock_method)|释放 `mutex` 的所有权。|  
  
## <a name="requirements"></a>要求  
 **标头：**mutex  
  
 **命名空间：** std  
  
##  <a name="a-namerecursivetimedmutexlockmethoda--lock"></a><a name="recursive_timed_mutex__lock_method"></a>lock  
 阻止调用线程，直到线程获取 `mutex` 的所有权。  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>备注  
 如果调用线程已拥有 `mutex`，则该方法将立即返回，同时上一锁定保持有效。  
  
##  <a name="a-namerecursivetimedmutexrecursivetimedmutexconstructora--recursivetimedmutex-constructor"></a><a name="recursive_timed_mutex__recursive_timed_mutex_constructor"></a>  recursive_timed_mutex 构造函数  
 构造未锁定的 `recursive_timed_mutex` 对象。  
  
```cpp  
recursive_timed_mutex();
```  
  
##  <a name="a-namerecursivetimedmutexdtorrecursivetimedmutexdestructora--recursivetimedmutex-destructor"></a><a name="recursive_timed_mutex___dtorrecursive_timed_mutex_destructor"></a>  ~recursive_timed_mutex 析构函数  
 释放由 `recursive_timed_mutex` 对象使用的任何资源。  
  
```cpp  
~recursive_timed_mutex();
```  
  
### <a name="remarks"></a>备注  
 如果当析构函数运行时对象被锁定，则该行为不确定。  
  
##  <a name="a-namerecursivetimedmutextrylockmethoda--trylock"></a><a name="recursive_timed_mutex__try_lock_method"></a>try_lock  
 在不阻止的情况下尝试获取 `mutex` 的所有权。  
  
```cpp  
bool try_lock() noexcept;
```  
  
### <a name="return-value"></a>返回值  
 如果此方法成功获取 `mutex` 的所有权，或如果调用线程已拥有 `mutex`，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 如果调用线程已拥有 `mutex`，则该函数将立即返回 `true`，并且上一锁定一直保持有效。  
  
##  <a name="a-namerecursivetimedmutextrylockformethoda--trylockfor"></a><a name="recursive_timed_mutex__try_lock_for_method"></a>try_lock_for  
 在不阻止的情况下尝试获取 `mutex` 的所有权。  
  
```cpp  
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```  
  
### <a name="parameters"></a>参数  
 `Rel_time`  
 一个 [chrono::duration](../standard-library/duration-class.md) 对象，指定此方法尝试获取 `mutex` 所有权的最大时间量。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功获取 `mutex` 的所有权，或如果调用线程已拥有 `mutex`，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 如果调用线程已拥有 `mutex`，则该方法将立即返回 `true`，同时上一锁定保持有效。  
  
##  <a name="a-namerecursivetimedmutextrylockuntilmethoda--trylockuntil"></a><a name="recursive_timed_mutex__try_lock_until_method"></a>try_lock_until  
 在不阻止的情况下尝试获取 `mutex` 的所有权。  
  
```cpp  
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```  
  
### <a name="parameters"></a>参数  
 `Abs_time`  
 一个时间点，指定阈值，在此之后此方法不再尝试获取 `mutex` 所有权。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功获取 `mutex` 的所有权，或如果调用线程已拥有 `mutex`，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 如果调用线程已拥有 `mutex`，则该方法将立即返回 `true`，同时上一锁定保持有效。  
  
##  <a name="a-namerecursivetimedmutexunlockmethoda--unlock"></a><a name="recursive_timed_mutex__unlock_method"></a>unlock  
 释放 `mutex` 的所有权。  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>备注  
 仅当 `mutex` 的调用次数与在 `recursive_timed_mutex` 对象上成功调用 [lock](#recursive_timed_mutex__lock_method)、[try_lock](#recursive_timed_mutex__try_lock_method)、[try_lock_for](#recursive_timed_mutex__try_lock_for_method) [try_lock_until](#recursive_timed_mutex__try_lock_until_method) 的次数一样多时，此方法才释放其所有权。  
  
 如果调用的线程不拥有 `mutex`，则该行为不确定。  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)




