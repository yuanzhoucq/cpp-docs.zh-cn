---
title: "condition_variable 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- condition_variable/std::condition_variable
dev_langs:
- C++
ms.assetid: 80b1295c-b73d-4d46-b664-6e183f2eec1b
caps.latest.revision: 16
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
ms.openlocfilehash: 6ba1c9aae256029cc35f1815dbc7bfd3503254dc
ms.lasthandoff: 02/24/2017

---
# <a name="conditionvariable-class"></a>condition_variable 类
使用 `condition_variable` 类在具有 `mutex` 类型的 `unique_lock<mutex>` 时等待事件。 此类型的对象的性能可能比 [condition_variable_any<unique_lock\<mutex>>](../standard-library/condition-variable-any-class.md) 类型的对象更好。  
  
## <a name="syntax"></a>语法  
  
```
class condition_variable;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[condition_variable::condition_variable 构造函数](#condition_variable__condition_variable_constructor)|构造 `condition_variable` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[condition_variable::native_handle 方法](#condition_variable__native_handle_method)|返回表示 condition_variable 句柄的特定于实现的类型。|  
|[condition_variable::notify_all](#condition_variable__notify_all_method)|取消阻止正在等待 `condition_variable` 对象的所有线程。|  
|[condition_variable::notify_one](#condition_variable__notify_one_method)|取消阻止正在等待 `condition_variable` 对象的某个线程。|  
|[condition_variable::wait](#condition_variable__wait_method)|阻止线程。|  
|[condition_variable::wait_for](#condition_variable__wait_for_method)|阻止某个线程，并设置线程阻止的时间间隔。|  
|[condition_variable::wait_until](#condition_variable__wait_until_method)|阻止某个线程，并设置线程阻止的最大时间点。|  
  
## <a name="requirements"></a>要求  
 **标头：** condition_variable  
  
 **命名空间：** std  
  
##  <a name="a-nameconditionvariableconditionvariableconstructora--conditionvariableconditionvariable-constructor"></a><a name="condition_variable__condition_variable_constructor"></a>  condition_variable::condition_variable 构造函数  
 构造 `condition_variable` 对象。  
  
```
condition_variable();
```  
  
### <a name="remarks"></a>备注  
 如果没有足够的内存，构造函数将抛出包含 `not_enough_memory` 错误代码的 [system_error](../standard-library/system-error-class.md) 对象。 如果由于某些其他资源不可用导致无法构造该对象，则构造函数将抛出包含 `resource_unavailable_try_again` 错误代码的 `system_error` 对象。  
  
##  <a name="a-nameconditionvariablenativehandlemethoda--conditionvariablenativehandle"></a><a name="condition_variable__native_handle_method"></a>  condition_variable::native_handle  
 返回表示 condition_variable 句柄的特定于实现的类型。  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>返回值  
 `native_handle_type` 被定义为指向并发运行时内部数据结构的指针。  
  
##  <a name="a-nameconditionvariablenotifyallmethoda--conditionvariablenotifyall"></a><a name="condition_variable__notify_all_method"></a>  condition_variable::notify_all  
 取消阻止正在等待 `condition_variable` 对象的所有线程。  
  
```
void notify_all() noexcept;
```  
  
##  <a name="a-nameconditionvariablenotifyonemethoda--conditionvariablenotifyone"></a><a name="condition_variable__notify_one_method"></a>  condition_variable::notify_one  
 取消阻止正在 `condition_variable` 对象上等待的某个线程。  
  
```
void notify_one() noexcept;
```  
  
##  <a name="a-nameconditionvariablewaitmethoda--conditionvariablewait"></a><a name="condition_variable__wait_method"></a>  condition_variable::wait  
 阻止线程。  
  
```
void wait(unique_lock<mutex>& Lck);

template <class Predicate>
void wait(unique_lock<mutex>& Lck, Predicate Pred);
```  
  
### <a name="parameters"></a>参数  
 `Lck`  
 [unique_lock\<mutex>](../standard-library/unique-lock-class.md) 对象。  
  
 `Pred`  
 返回 `true` 或 `false` 的任何表达式。  
  
### <a name="remarks"></a>备注  
 第一种方法进行阻止，直到通过调用 [notify_one](#condition_variable__notify_one_method) 或 [notify_all](#condition_variable__notify_all_method) 对 `condition_variable` 对象发出信号。 它还可错误唤醒。  
  
 第二种方法实际上执行以下代码。  
  
```cpp  
while(!Pred())
    wait(Lck);
```    
  
##  <a name="a-nameconditionvariablewaitformethoda--conditionvariablewaitfor"></a><a name="condition_variable__wait_for_method"></a>  condition_variable::wait_for  
 阻止某个线程，并设置线程阻止的时间间隔。  
  
```
template <class Rep, class Period>
cv_status wait_for(
    unique_lock<mutex>& Lck,
    const chrono::duration<Rep, Period>& Rel_time);

template <class Rep, class Period, class Predicate>
bool wait_for(
    unique_lock<mutex>& Lck,
    const chrono::duration<Rep, Period>& Rel_time, 
    Predicate Pred);
```  
  
### <a name="parameters"></a>参数  
 `Lck`  
 [unique_lock\<mutex>](../standard-library/unique-lock-class.md) 对象。  
  
 `Rel_time`  
 `chrono::duration` 对象指定线程唤醒前的时间。  
  
 `Pred`  
 返回 `true` 或 `false` 的任何表达式。  
  
### <a name="return-value"></a>返回值  
 如果在已用 `Rel_time` 时间时等待终止，则第一种方法返回 `cv_status::timeout`。 否则，该方法将返回 `cv_status::no_timeout`。  
  
 第二种方法返回值 `Pred`。  
  
### <a name="remarks"></a>备注  
 第一种方法进行阻止，直到通过调用 [notify_one](#condition_variable__notify_one_method) 或 [notify_all](#condition_variable__notify_all_method) 对 `condition_variable` 对象发出信号，或直到已用 `Rel_time` 时间间隔。 它还可错误唤醒。  
  
 第二种方法实际上执行以下代码。  
  
```cpp  
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```  
  
##  <a name="a-nameconditionvariablewaituntilmethoda--conditionvariablewaituntil"></a><a name="condition_variable__wait_until_method"></a>  condition_variable::wait_until  
 阻止某个线程，并设置线程阻止的最大时间点。  
  
```
template <class Clock, class Duration>
cv_status wait_until(
    unique_lock<mutex>& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time);

template <class Clock, class Duration, class Predicate>
bool wait_until(
    unique_lock<mutex>& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time, 
    Predicate Pred);

cv_status wait_until(
    unique_lock<mutex>& Lck,
    const xtime* Abs_time);

template <class Predicate>
bool wait_until(
    unique_lock<mutex>& Lck,
    const xtime* Abs_time, 
    Predicate Pred);
```  
  
### <a name="parameters"></a>参数  
 `Lck`  
 [unique_lock\<mutex>](../standard-library/unique-lock-class.md) 对象。  
  
 `Abs_time`  
 [chrono::time_point](../standard-library/time-point-class.md) 对象。  
  
 `Pred`  
 返回 `true` 或 `false` 的任何表达式。  
  
### <a name="return-value"></a>返回值  
 如果在已用 `Abs_time` 时间时等待终止，则返回 `cv_status` 类型的方法返回 `cv_status::timeout`。 否则，方法返回 `cv_status::no_timeout`。  
  
 返回 `bool` 的方法返回值 `Pred`。  
  
### <a name="remarks"></a>备注  
 第一种方法进行阻止，直到通过调用 [notify_one](#condition_variable__notify_one_method) 或 [notify_all](#condition_variable__notify_all_method) 对 `condition_variable` 对象发出信号，或直到 `Abs_time`。 它还可错误唤醒。  
  
 第二种方法实际上执行以下代码  
  
```cpp  
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```  
  
 第三种和第四种方法使用指向 `xtime` 类型的对象的指针来替换 `chrono::time_point` 对象。 `xtime` 对象指定等待信号的最大时间。  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [<condition_variable>](../standard-library/condition-variable.md)




