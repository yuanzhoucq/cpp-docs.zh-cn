---
title: "promise 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
dev_langs:
- C++
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 4cc20303a02fbf21fd54e18569f964e268809439
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="promise-class"></a>promise 类
介绍*异步提供程序*。  
  
## <a name="syntax"></a>语法  
  
```
template <class Ty>
class promise;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[承诺](#promise)|构造 `promise` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[get_future](#get_future)|返回与此 promise 关联的 [future](../standard-library/future-class.md)。|  
|[set_exception](#set_exception)|以原子方式设置此 promise 的结果以指示异常。|  
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|以原子方式设置此 promise 的结果以指示异常，并且仅在销毁当前线程中的所有线程本地对象后（通常在线程退出时）发出通知。|  
|[set_value](#set_value)|以原子方式设置此 promise 的结果以指示值。|  
|[set_value_at_thread_exit](#set_value_at_thread_exit)|以原子方式设置此 promise 的结果以指示值，并且仅在销毁当前线程中的所有线程本地对象后（通常在线程退出时）发出通知。|  
|[swap](#swap)|用指定的 promise 对象的*关联的异步状态*交换此 promise 的关联的异步状态。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[promise::operator=](#op_eq)|此 promise 对象的共享状态的分配。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `promise`  
  
## <a name="requirements"></a>要求  
 **标头：** \<将来 >  
  
 **命名空间：** std  
  
##  <a name="get_future"></a>promise::get_future  
 返回具有与此 promise 相同的*关联异步状态*的 [future](../standard-library/future-class.md) 对象。  
  
```
future<Ty> get_future();
```  
  
### <a name="remarks"></a>备注  
 如果 promise 对象为空，则此方法将引发一个 [error_code](../standard-library/error-code-class.md) 为 `no_state` 的 [future_error](../standard-library/future-error-class.md)。  
  
 如果此方法已调用具有相同关联异步状态的承诺对象，则此方法将引发 `future_error` 为 `error_code` 的 `future_already_retrieved`。  
  
##  <a name="op_eq"></a>promise::operator=  
 从指定的 `promise` 对象传输*关联异步状态*。  
  
```
promise& operator=(promise&& Other) noexcept;
```  
  
### <a name="parameters"></a>参数  
 `Other`  
 一个 `promise` 对象。  
  
### <a name="return-value"></a>返回值  
 `*this`  
  
### <a name="remarks"></a>备注  
 此运算符从 `Other` 传输关联异步状态。 传输后，`Other` 为空。  
  
##  <a name="promise"></a>promise::promise 构造函数  
 构造 `promise` 对象。  
  
```
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```  
  
### <a name="parameters"></a>参数  
 `Al`  
 内存分配器。 有关详细信息，请参见 [\<allocators>](../standard-library/allocators-header.md)。  
  
 `Other`  
 一个 `promise` 对象。  
  
### <a name="remarks"></a>备注  
 第一个构造函数构造一个*空*`promise`对象。  
  
 第二个构造函数构造一个空 `promise` 对象，并使用 `Al` 实现内存分配。  
  
 第三个构造函数构造 `promise` 对象并从 `Other` 传输关联异步状态，同时保留 `Other` 为空。  
  
##  <a name="set_exception"></a>promise::set_exception  
 以原子方式将异常存储为此 `promise` 对象的结果，并将“关联的异步状态”设置为“就绪”。  
  
```
void set_exception(exception_ptr Exc);
```  
  
### <a name="parameters"></a>参数  
 `Exc`  
 通过此方法另存为异常结果的 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)。  
  
### <a name="remarks"></a>备注  
 如果 `promise` 对象没有关联的异步状态，则此方法将引发具有错误代码 `no_state` 的 [future_error](../standard-library/future-error-class.md)。  
  
 如果已为具有相同的关联异步状态的 `promise` 对象调用 `set_exception`、[set_exception_at_thread_exit](#set_exception_at_thread_exit)、[set_value](#set_value) 或 [set_value_at_thread_exit](#set_value_at_thread_exit)，则此方法将引发具有错误代码 `promise_already_satisfied` 的 `future_error`。  
  
 此方法的结果是，不再阻止在关联的异步状态上受阻的任何线程。  
  
##  <a name="set_exception_at_thread_exit"></a>promise::set_exception_at_thread_exit  
 以原子方式设置此 `promise` 的结果以指示异常，并且仅在当前线程中的所有线程本地对象被销毁后（通常在线程退出时）发出通知。  
  
```
void set_exception_at_thread_exit(exception_ptr Exc);
```  
  
### <a name="parameters"></a>参数  
 `Exc`  
 通过此方法另存为异常结果的 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)。  
  
### <a name="remarks"></a>备注  
 如果 promise 对象没有关联的异步状态，则此方法将引发具有错误代码 `no_state` 的 [future_error](../standard-library/future-error-class.md)。  
  
 如果已为具有相同的关联异步状态的 `promise` 对象调用 [set_exception](#set_exception)、`set_exception_at_thread_exit`、[set_value](#set_value) 或 [set_value_at_thread_exit](#set_value_at_thread_exit)，则此方法将引发具有错误代码 `promise_already_satisfied` 的 `future_error`。  
  
 与 [set_exception](#set_exception) 相反，此方法在当前线程中的所有线程本地对象被销毁前不会将关联的异步状态设置为已就绪。 通常，在关联的异步状态上受阻的线程会受到阻止，直到当前线程退出。  
  
##  <a name="set_value"></a>promise::set_value  
 以原子方式将值存储为此 `promise` 对象的结果，并将“关联的异步状态”设置为“就绪”。  
  
```
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```  
  
### <a name="parameters"></a>参数  
 `Val`  
 要存储为结果的值。  
  
### <a name="remarks"></a>备注  
 如果 `promise` 对象没有关联的异步状态，则此方法将引发具有错误代码 `no_state` 的 [future_error](../standard-library/future-error-class.md)。  
  
 如果已为具有相同的关联异步状态的 `promise` 对象调用 [set_exception](#set_exception)、[set_exception_at_thread_exit](#set_exception_at_thread_exit)、`set_value` 或 [set_value_at_thread_exit](#set_value_at_thread_exit)，则此方法将引发具有错误代码 `promise_already_satisfied` 的 `future_error`。  
  
 此方法的结果是，不再阻止在关联的异步状态上受阻的任何线程。  
  
 第一种方法还会引发在将 `Val` 复制到关联的异步状态时所引发的任何异常。 在此情况下，关联的异步状态不设置为“就绪”。  
  
 第二种方法还会引发在将 `Val` 移动到关联的异步状态时引发的任何异常。 在此情况下，关联的异步状态不设置为“就绪”。  
  
 对于部分专用化 `promise<Ty&>`，存储的值实际上是对 `Val` 的引用。  
  
 对于专用化 `promise<void>`，不存在任何存储的值。  
  
##  <a name="set_value_at_thread_exit"></a>promise::set_value_at_thread_exit  
 以原子方式将值存为此 `promise` 对象的结果。  
  
```
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```  
  
### <a name="parameters"></a>参数  
 `Val`  
 要存储为结果的值。  
  
### <a name="remarks"></a>备注  
 如果 promise 对象没有关联的异步状态，则此方法将引发具有错误代码 `no_state` 的 [future_error](../standard-library/future-error-class.md)。  
  
 如果已为具有相同的关联异步状态的 `promise` 对象调用 [set_exception](#set_exception)、[set_exception_at_thread_exit](#set_exception_at_thread_exit)、[set_value](#set_value) 或 `set_value_at_thread_exit`，则此方法将引发具有错误代码 `promise_already_satisfied` 的 `future_error`。  
  
 与 `set_value` 相反，在当前线程中的所有线程本地对象被销毁前不会将关联的异步状态设置为已就绪。 通常，在关联的异步状态上受阻的线程会受到阻止，直到当前线程退出。  
  
 第一种方法还会引发在将 `Val` 复制到关联的异步状态时所引发的任何异常。  
  
 第二种方法还会引发在将 `Val` 移动到关联的异步状态时引发的任何异常。  
  
 对于部分专用化 `promise<Ty&>`，存储的值实际上是对 `Val` 的引用。  
  
 对于专用化 `promise<void>`，不存在任何存储的值。  
  
##  <a name="swap"></a>promise::swap  
 将此 promise 对象的*关联异步状态*与指定对象的交换。  
  
```
void swap(promise& Other) noexcept;
```  
  
### <a name="parameters"></a>参数  
 `Other`  
 一个 `promise` 对象。  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)




 


