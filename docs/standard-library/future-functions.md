---
title: "&lt;future&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e3acc1e-736a-42dc-ade2-b2fe69aa96bc
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 57a9e0ba45c363d126ef44dc80eeb13d72b3733d
ms.lasthandoff: 02/24/2017

---
# <a name="ltfuturegt-functions"></a>&lt;future&gt; 函数
||||  
|-|-|-|  
|[async](#async_function)|[future_category](#future_category_function)|[make_error_code](#make_error_code_function)|  
|[make_error_condition](#make_error_condition_function)|[swap](#swap_function)|  
  
##  <a name="a-nameasyncfunctiona--async"></a><a name="async_function"></a>async  
 表示一个异步提供程序。  
  
```
template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(Fn&& fn, ArgTypes&&... args);

template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(launch policy, Fn&& fn, ArgTypes&&... args);
```  
  
### <a name="parameters"></a>参数  
 `policy`  
 一个 [launch](../standard-library/future-enums.md#launch_enumeration) 值。  
  
### <a name="remarks"></a>备注  
 缩写的定义：  
  
|||  
|-|-|  
|*dfn*|调用 `decay_copy(forward<Fn>(fn))` 的结果。|  
|*dargs*|调用 `decay_copy(forward<ArgsTypes>(args…))` 的结果。|  
|*Ty*|`result_of<Fn(ArgTypes…)>::type` 类型。|  
  
 第一个模板函数返回 `async(launch::any, fn, args…)`。  
  
 第二个函数返回一个 `future<Ty>` 对象，其关联的异步状态包含一个结果以及 dfn 和 dargs 的值和一个用于管理单独的执行线程的线程对象。  
  
 除非 `decay<Fn>::type` 是一种不同于 launch 的类型，否则第二个函数将不参与重载解析。  
  
 如果 `policy` 是 `launch::any`，则函数可能会选择 `launch::async` 或 `launch::deferred`。 在此实现中，函数将使用 `launch::async`。  
  
 如果 `policy` 是 `launch::async`，则函数将创建一个计算 `INVOKE(dfn, dargs..., Ty)` 的线程。 函数创建线程后将返回，而不等待结果。 如果系统无法启动新线程，则函数将引发一个错误代码为 `resource_unavailable_try_again` 的 [system_error](../standard-library/system-error-class.md)。  
  
 如果 `policy` 为 `launch::deferred`，则函数会将其关联异步状态标记为包含一个延迟函数并返回。 对任何等待关联异步状态生效的非计时函数的第一次调用都将通过计算 `INVOKE(dfn, dargs..., Ty)` 来调用延迟函数。  
  
 任何情况下，在通过引发异常或正常返回完成 `INVOKE(dfn, dargs…, Ty)` 的计算之前，`future` 对象的关联异步状态不会设置为就绪。 如果引发了异常，则关联异步状态的结果为异常，否则为计算返回的任何值。  
  
> [!NOTE]
>  对于一个附加到以 `std::async` 开头的任务的 `future`（或最后一个 [shared_future](../standard-library/shared-future-class.md)），如果任务尚未完成，则析构函数将阻塞；即，如果此线程尚未调用 `.get()` 或 `.wait()` 且任务仍在进行，则析构函数将阻塞。 如果从 `future` 中获得的 `std::async` 移出局部范围，则使用它的其他代码必须知道其析构函数可能在共享状态变成已就绪时阻塞。  
  
 伪函数 `INVOKE` 定义在 [\<functional>](../standard-library/functional.md) 中。  
  
##  <a name="a-namefuturecategoryfunctiona--futurecategory"></a><a name="future_category_function"></a>future_category  
 返回一个描述与 `future` 对象相关联错误特征的 [error_category](../standard-library/error-category-class.md) 对象的引用。  
  
```
const error_category& future_category() noexcept;
```  
  
##  <a name="a-namemakeerrorcodefunctiona--makeerrorcode"></a><a name="make_error_code_function"></a>make_error_code  
 创建一个 [error_code](../standard-library/error-code-class.md) 以及一个描述 [future](../standard-library/future-class.md) 错误特征的 [error_category](../standard-library/error-category-class.md) 对象。  
  
```
inline error_code make_error_code(future_errc Errno) noexcept;
```  
  
### <a name="parameters"></a>参数  
 `Errno`  
 一个标识已报告错误的 [future_errc](../standard-library/future-enums.md#future_errc_enumeration) 值。  
  
### <a name="return-value"></a>返回值  
 `error_code(static_cast<int>(Errno), future_category());`  
  
##  <a name="a-namemakeerrorconditionfunctiona--makeerrorcondition"></a><a name="make_error_condition_function"></a>make_error_condition  
 创建一个 [error_condition](../standard-library/error-condition-class.md) 以及一个描述 [future](../standard-library/future-class.md) 错误特征的 [error_category](../standard-library/error-category-class.md) 对象。  
  
```
inline error_condition make_error_condition(future_errc Errno) noexcept;
```  
  
### <a name="parameters"></a>参数  
 `Errno`  
 一个标识已报告错误的 [future_errc](../standard-library/future-enums.md#future_errc_enumeration) 值。  
  
### <a name="return-value"></a>返回值  
 `error_condition(static_cast<int>(Errno), future_category());`  
  
##  <a name="a-nameswapfunctiona--swap"></a><a name="swap_function"></a>swap  
 将一个 `promise` 对象的关联异步状态与另一对象的关联异步状态交换。  
  
```
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 左 `promise` 对象。  
  
 `Right`  
 正确的 `promise` 对象。  
  
## <a name="see-also"></a>另请参阅  
 [\<future>](../standard-library/future.md)




