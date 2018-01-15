---
title: "structured_task_group 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
dev_langs: C++
helpviewer_keywords: structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ae2e4648e94d05edc3ec787232bab7f1db8aea90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="structuredtaskgroup-class"></a>structured_task_group 类
`structured_task_group` 类表示并行工作的高度结构化集合。 可以使用 `task_handle` 对象将各个并行任务排队到 `structured_task_group` 并等待它们完成，或在它们完成执行之前取消任务组，这将中止尚未开始执行的所有任务。  
  
## <a name="syntax"></a>语法  
  
```
class structured_task_group;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[structured_task_group](#ctor)|已重载。 构造一个新`structured_task_group`对象。|  
|[~ structured_task_group 析构函数](#dtor)|销毁 `structured_task_group` 对象。 你应该调用`wait`或`run_and_wait`之前析构函数执行的对象上的方法除非析构函数正在执行的结果堆栈展开由于出现异常。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[取消](#cancel)|使最大努力尝试取消任务组取得 root 权限的工作的子树。 对任务组计划每个任务都将获取取消间接如有可能。|  
|[is_canceling](#is_canceling)|任务组当前正在取消通知调用方。 这不一定表示，`cancel`上调用了方法`structured_task_group`对象 (虽然这样肯定会让此方法以返回`true`)。 它可能是这种情况，`structured_task_group`对象正在进行内联执行，任务组进一步向上工作树中已被取消。 在如这些位置的情况下运行时可以确定取消将流过提前`structured_task_group`对象，`true`也会返回。|  
|[run](#run)|已重载。 在计划任务`structured_task_group`对象。 调用方管理的生存期`task_handle`传入的对象`_Task_handle`参数。 采用参数 `_Placement` 的版本会导致任务偏向在该参数指定的位置执行。|  
|[run_and_wait](#run_and_wait)|已重载。 计划任务以运行内联将在调用上下文的帮助下`structured_task_group`完整取消支持的对象。 如果`task_handle`对象作为参数传递`run_and_wait`，调用方负责管理的生存期`task_handle`对象。 该函数然后等待，直到上的所有工作`structured_task_group`对象已完成或已取消。|  
|[等待](#wait)|等待，直到上的所有工作`structured_task_group`已完成或已取消。|  
  
## <a name="remarks"></a>备注  
 有大量的使用情况的严格限制`structured_task_group`以便获得的性能对象：  
  
-   单个`structured_task_group`对象不能由多个线程。 上的所有操作`structured_task_group`对象必须由创建该对象的线程执行。 此规则的两个例外是成员函数`cancel`和`is_canceling`。 对象可能不是 lambda 表达式的捕获列表中，并且使用任务中,，除非该任务使用某一取消操作。  
  
-   安排到的所有任务`structured_task_group`对象计划使用`task_handle`对象必须显式管理的生存期。  
  
-   多个组可能只用于按绝对嵌套顺序。 如果两个`structured_task_group`声明对象，第二个正在声明 （内部一个） 必须在任何方法，但之前析构`cancel`或`is_canceling`上的第一个调用 （外部一个）。 此条件为 true 这两种情况下只需声明多个`structured_task_group`对象中的相同或功能嵌套作用域，以及排队时起到的任务的大小写`structured_task_group`通过`run`或`run_and_wait`方法。  
  
-   与常规不同`task_group`类中的所有状态`structured_task_group`都类是最终版。 已将任务排队到组并等待它们完成后，你可能不会再次使用同一个组。  
  
 有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `structured_task_group`  
  
## <a name="requirements"></a>惠?  
 **标头：** ppl.h  
  
 **命名空间：** 并发  
  
##  <a name="cancel"></a>取消 

 使最大努力尝试取消任务组取得 root 权限的工作的子树。 对任务组计划每个任务都将获取取消间接如有可能。  
  
```
void cancel();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。  
  
##  <a name="is_canceling"></a>is_canceling 

 任务组当前正在取消通知调用方。 这不一定表示，`cancel`上调用了方法`structured_task_group`对象 (虽然这样肯定会让此方法以返回`true`)。 它可能是这种情况，`structured_task_group`对象正在进行内联执行，任务组进一步向上工作树中已被取消。 在如这些位置的情况下运行时可以确定取消将流过提前`structured_task_group`对象，`true`也会返回。  
  
```
bool is_canceling();
```  
  
### <a name="return-value"></a>返回值  
 相对值的指示是否`structured_task_group`对象处于取消 （或保证功能很快即可）。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。  
  
##  <a name="run"></a>运行 

 在计划任务`structured_task_group`对象。 调用方管理的生存期`task_handle`传入的对象`_Task_handle`参数。 采用参数 `_Placement` 的版本会导致任务偏向在该参数指定的位置执行。  
  
```
template<class _Function>
void run(
    task_handle<_Function>& _Task_handle);

template<class _Function>
void run(
    task_handle<_Function>& _Task_handle,
    location& _Placement);
```  
  
### <a name="parameters"></a>参数  
 `_Function`  
 将调用以执行的任务句柄的主体的函数对象类型。  
  
 `_Task_handle`  
 正在计划的工作句柄。 请注意，调用方负责此对象的生存期。 运行时将继续预期会存留，直至`wait`或`run_and_wait`方法已调用此`structured_task_group`对象。  
  
 `_Placement`  
 对应执行 `_Task_handle` 参数所表示任务的位置的引用。  
  
### <a name="remarks"></a>备注  
 运行时创建一份工作函数传递给此方法。 将传递给此方法的函数对象中发生的任何状态更改不会显示在该函数对象的副本。  
  
 如果`structured_task_group`因堆栈展开从异常的结果，则你不需要保证，调用已为`wait`或`run_and_wait`方法。 在这种情况下，析构函数将适当地取消并等待任务由`_Task_handle`参数来完成。  
  
 引发[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)如果任务处理的异常由给定`_Task_handle`参数已安排到一个任务组对象通过`run`方法并已对任何干预调用请`wait`或`run_and_wait`该任务组上的方法。  
  
##  <a name="run_and_wait"></a>run_and_wait 

 计划任务以运行内联将在调用上下文的帮助下`structured_task_group`完整取消支持的对象。 如果`task_handle`对象作为参数传递`run_and_wait`，调用方负责管理的生存期`task_handle`对象。 该函数然后等待，直到上的所有工作`structured_task_group`对象已完成或已取消。  
  
```
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```  
  
### <a name="parameters"></a>参数  
 `_Function`  
 将调用以执行任务的函数对象的类型。  
  
 `_Task_handle`  
 将在调用上下文以内联方式运行该任务句柄。 请注意，调用方负责此对象的生存期。 运行时将继续预期会存留，直至`run_and_wait`方法完成执行。  
  
 `_Func`  
 一个函数，将调用来调用该工作的正文。 这可能是 lambda 或其他对象，支持具有签名的函数调用运算符的版本`void operator()()`。  
  
### <a name="return-value"></a>返回值  
 相对值的指示是否在等待是否符合要求或任务组已取消，由于显式取消操作或从一个其任务会引发异常。 有关详细信息，请参阅[task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>备注  
 请注意，其中一个或多个任务安排到`structured_task_group`对象可能会执行将在调用上下文的内联。  
  
 如果一个或多个任务安排到`structured_task_group`对象引发了异常，运行时将选择其选择的一个此类异常并将其传播到调用`run_and_wait`方法。  
  
 返回此函数后，`structured_task_group` 对象被视为处于最终状态，并且不应使用。 请注意该之后的利用率`run_and_wait`方法返回将导致未定义的行为。  
  
 在执行非异常路径中，您可以调用此方法或`wait`方法之前的析构函数`structured_task_group`执行。  
  
##  <a name="ctor"></a>structured_task_group 

 构造一个新`structured_task_group`对象。  
  
```
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```  
  
### <a name="parameters"></a>参数  
 `_CancellationToken`  
 与此结构化的任务组相关联的取消标记。 取消标记时，将会取消的结构化的任务组。  
  
### <a name="remarks"></a>备注  
 采用取消标记的构造函数会创建一个在取消与标记相关联的源时将会取消的 `structured_task_group`。 提供显式取消标记也可以避免此结构化的任务组参与采用不同标记或没有标记的父组的隐式取消。  
  
##  <a name="dtor"></a>~ structured_task_group 

 销毁 `structured_task_group` 对象。 你应该调用`wait`或`run_and_wait`之前析构函数执行的对象上的方法除非析构函数正在执行的结果堆栈展开由于出现异常。  
  
```
~structured_task_group();
```  
  
### <a name="remarks"></a>备注  
 如果析构函数导致正常执行过程中 （例如，不堆栈展开由于出现异常） 且运行`wait`也不`run_and_wait`在调用方法，析构函数可能会引发[missing_wait](missing-wait-class.md)异常。  
  
##  <a name="wait"></a>等待 

 等待，直到上的所有工作`structured_task_group`已完成或已取消。  
  
```
task_group_status wait();
```  
  
### <a name="return-value"></a>返回值  
 相对值的指示是否在等待是否符合要求或任务组已取消，由于显式取消操作或从一个其任务会引发异常。 有关详细信息，请参阅[task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>备注  
 请注意，其中一个或多个任务安排到`structured_task_group`对象可能会执行将在调用上下文的内联。  
  
 如果一个或多个任务安排到`structured_task_group`对象引发了异常，运行时将选择其选择的一个此类异常并将其传播到调用`wait`方法。  
  
 返回此函数后，`structured_task_group` 对象被视为处于最终状态，并且不应使用。 请注意该之后的利用率`wait`方法返回将导致未定义的行为。  
  
 在执行非异常路径中，您可以调用此方法或`run_and_wait`方法之前的析构函数`structured_task_group`执行。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [task_group 类](task-group-class.md)   
 [task_handle 类](task-handle-class.md)
