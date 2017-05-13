---
title: "thread 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- thread/std::thread
- thread/std::thread::id Class
- thread/std::thread::thread
- thread/std::thread::detach
- thread/std::thread::get_id
- thread/std::thread::hardware_concurrency
- thread/std::thread::join
- thread/std::thread::joinable
- thread/std::thread::native_handle
- thread/std::thread::swap
dev_langs:
- C++
ms.assetid: df249bc7-ff81-4ff9-a6d6-5e3d9a8f56a1
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: b1c5282d284a70917c6c14511bacda305180d778
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="thread-class"></a>thread 类
定义用于查看和管理应用程序中执行线程的对象。  
  
## <a name="syntax"></a>语法  
  
```
class thread;
```  
  
## <a name="remarks"></a>备注  
 可以使用 `thread` 对象查看和管理应用程序中的执行线程。 使用默认构造函数创建的线程对象不与任何执行线程相关联。 通过使用可调用对象构造的线程对象创建一个新的执行线程，并在该线程中调用可调用对象。 可移动线程对象，但不能复制。 因此，执行线程只与一个线程对象相关联。  
  
 每个执行线程都具有 `thread::id` 类型的唯一标识符。 函数 `this_thread::get_id` 返回调用线程的标识符。 成员函数`thread::get_id` 返回由线程对象管理的线程标识符。 对于默认构造的线程对象，`thread::get_id` 方法返回具有值的对象，该值与所有默认构造线程对象的值相同但和 `this_thread::get_id` 返回的任何线程（可在调用时连接）的值不同。  
  
## <a name="members"></a>成员  
  
### <a name="public-classes"></a>公共类  
  
|名称|描述|  
|----------|-----------------|  
|[thread::id Class](#id_class)|标识唯一关联的线程。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[thread](#thread)|构造 `thread` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[分离](#detach)|从 `thread` 对象拆离相关联的线程。|  
|[get_id](#get_id)|返回关联线程的唯一标识符。|  
|[hardware_concurrency](#hardware_concurrency)|静态。 返回硬件线程上下文的估计数量。|  
|[join](#join)|阻止，直到完成关联的线程。|  
|[加入](#joinable)|指定关联的线程是否可联接。|  
|[native_handle](#native_handle)|返回表示线程句柄的特定于实现的类型。|  
|[swap](#swap)|与指定的 `thread` 对象交换对象状态。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[thread::operator=](#op_eq)|将线程与当前 `thread` 对象关联。|  
  
## <a name="requirements"></a>要求  
 **标头︰** \<线程 >  
  
 **命名空间：** std  
  
##  <a name="detach"></a>thread:: detach
 拆离相关联的线程。 操作系统负责释放终止的线程资源。  
  
```
void detach();
```  
  
### <a name="remarks"></a>备注  
 调用 `detach` 后，再调用 [get_id](#get_id)，返回[id](#id_class)。  
  
 如果与调用对象关联的线程不可联接，该函数将引发将引发一个错误代码为 `invalid_argument` 的 [system_error](../standard-library/system-error-class.md)。  
  
 如果与调用对象相关联的线程无效，该函数将引发将引发一个错误代码为 `no_such_process` 的 `system_error`。  
  
##  <a name="get_id"></a>thread:: get_id
 返回关联线程的唯一标识符。  
  
```
id get_id() const noexcept;
```  
  
### <a name="return-value"></a>返回值  
 一个 [thread:: id](#id_class) 对象，唯一标识相关联的线程，如果该对象没有任何关联的线程，则为 `thread::id()`。  
  
##  <a name="hardware_concurrency"></a>thread:: hardware_concurrency
 静态方法，返回硬件线程上下文数量的估计值。  
  
```
static unsigned int hardware_concurrency() noexcept;
```  
  
### <a name="return-value"></a>返回值  
 硬件线程上下文数量的估计值。 如果无法计算该值或该值未正确定义，此方法将返回 0。  
  
##  <a name="id_class"></a>  thread::id 类  
 为过程中的每个执行线程提供唯一标识符。  
  
```
class thread::id {
    id() noexcept;
};
```  
  
### <a name="remarks"></a>备注  
 默认构造函数创建一个对象，该对象与任何现有线程的 `thread::id` 对象都不相等。  
  
 所有默认构造的 `thread::id` 对象都相等。  
  
##  <a name="join"></a>thread:: join
 阻止，直到完成与调用对象相关联的执行线程。  
  
```
void join();
```  
  
### <a name="remarks"></a>备注  
 调用成功后，再继续调用 [get_id](#get_id)，以便调用对象返回默认值 [thread:: id](#id_class)，该默认值与任何现有线程的 `thread::id` 都不相等；如果调用不成功，`get_id` 返回的值保持不变。  
  
##  <a name="joinable"></a>thread:: joinable
 指定关联的线程是否可联接。  
  
```
bool joinable() const noexcept;
```  
  
### <a name="return-value"></a>返回值  
 如果关联的线程可联接，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 如果 `get_id() != id()`，则线程对象可联接。  
  
##  <a name="native_handle"></a>thread:: native_handle
 返回表示线程句柄的特定于实现的类型。 可以以特定于实现的方式使用线程句柄。  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>返回值  
 `native_handle_type` 被定义为可强制转化为 `void *` 的 Win32 `HANDLE`。  
  
##  <a name="op_eq"></a>thread::operator=  
 将指定对象的线程与当前对象相关联。  
  
```
thread& operator=(thread&& Other) noexcept;
```  
  
### <a name="parameters"></a>参数  
 `Other`  
 一个 `thread` 对象。  
  
### <a name="return-value"></a>返回值  
 `*this`  
  
### <a name="remarks"></a>备注  
 如果调用对象可联接，该方法会调用拆离。  
  
 建立关联后，将 `Other` 设置为默认构造状态。  
  
##  <a name="swap"></a>thread:: swap
 与指定的 `thread` 对象交换对象状态。  
  
```
void swap(thread& Other) noexcept;
```  
  
### <a name="parameters"></a>参数  
 `Other`  
 一个 `thread` 对象。  
  
##  <a name="thread"></a>  thread::thread 构造函数  
 构造 `thread` 对象。  
  
```
thread() noexcept;
template <class Fn, class... Args>
explicit thread(Fn&& F, Args&&... A);

thread(thread&& Other) noexcept;
```  
  
### <a name="parameters"></a>参数  
 `F`  
 要由线程执行的应用程序所定义的函数。  
  
 `A`  
 要传递到 `F` 的参数列表。  
  
 `Other`  
 一个现有的 `thread` 对象。  
  
### <a name="remarks"></a>备注  
 第一个构造函数构造与执行线程不相关联的对象。 通过调用 `get_id` 返回的构造对象的值为 `thread::id()`。  
  
 第二个构造函数构造一个对象，该对象与新的执行线程关联并执行在 [\<functional>](../standard-library/functional.md) 中定义的伪函数 `INVOKE`。 如果用于启动新线程的资源不足，该函数将引发一个错误代码为 `resource_unavailable_try_again` 的 [system_error](../standard-library/system-error-class.md) 对象。 如果对 `F` 的调用终止并捕获异常，则调用 [terminate](../standard-library/exception-functions.md#terminate)。  
  
 第三个构造函数将构造一个对象，该对象与关联 `Other` 的线程相关。 随后， `Other` 会被设置为默认构造状态。  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<thread>](../standard-library/thread.md)




