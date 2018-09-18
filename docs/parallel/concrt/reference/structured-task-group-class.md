---
title: structured_task_group 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
dev_langs:
- C++
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45daf3c2b2fe71d6e1954d489359e5ebe68ab54d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038589"
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
|[~ structured_task_group 析构函数](#dtor)|销毁 `structured_task_group` 对象。 你应该调用`wait`或`run_and_wait`之前析构函数执行的对象上的方法执行析构函数，除非为堆栈展开因异常而。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[取消](#cancel)|可以最大努力尝试取消的子树的根节点的此任务组的工作。 对任务组计划每个任务都将获取取消间接在可能的情况。|  
|[is_canceling](#is_canceling)|通知调用方任务组当前正在取消操作。 这不一定表示的`cancel`上调用了方法`structured_task_group`对象 (尽管这样肯定会让此方法以返回`true`)。 它可能发生此情况的`structured_task_group`对象正在执行内联和任务组进一步向上工作树中已取消。 在这些位置等的情况下运行时可以确定取消将流过提前`structured_task_group`对象，`true`也将返回。|  
|[run](#run)|已重载。 在计划任务`structured_task_group`对象。 调用方管理的生存期`task_handle`传入的对象`_Task_handle`参数。 采用参数 `_Placement` 的版本会导致任务偏向在该参数指定的位置执行。|  
|[run_and_wait](#run_and_wait)|已重载。 计划任务以运行内联将在调用上下文的帮助下`structured_task_group`完整的取消支持的对象。 如果`task_handle`对象作为参数传递`run_and_wait`，调用方负责管理的生存期`task_handle`对象。 然后函数等待直到上的所有工作`structured_task_group`对象已完成或已取消。|  
|[等待](#wait)|等待，直到上的所有工作`structured_task_group`已完成或已取消。|  
  
## <a name="remarks"></a>备注  
 有多种施加的使用情况的严重限制`structured_task_group`才能获得性能对象：  
  
-   单个`structured_task_group`对象不能由多个线程。 上的所有操作`structured_task_group`对象必须由创建该对象的线程。 此规则的两个例外是成员函数`cancel`和`is_canceling`。 对象可能无法在 lambda 表达式的捕获列表中，使用在任务中，除非该任务使用某个取消操作。  
  
-   为计划的所有任务`structured_task_group`对象计划使用`task_handle`对象必须显式管理的生存期。  
  
-   只可能绝对嵌套顺序使用多个组。 如果两个`structured_task_group`声明对象，第二个要声明 （内部一） 除外的任何方法之前必须析构`cancel`或`is_canceling`上第一个调用 （外部一个）。 此条件为 true，在这两种情况下声明多个`structured_task_group`中的相同或嵌套在功能上作用域，以及已排队的任务的大小写的对象`structured_task_group`通过`run`或`run_and_wait`方法。  
  
-   与常规不同`task_group`类中的所有状态`structured_task_group`都类不可更改。 已将任务排队到组并等待它们完成后，你可能不会再次使用同一个组。  
  
 有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `structured_task_group`  
  
## <a name="requirements"></a>要求  
 **标头：** ppl.h  
  
 **命名空间：** 并发  
  
##  <a name="cancel"></a> 取消 

 可以最大努力尝试取消的子树的根节点的此任务组的工作。 对任务组计划每个任务都将获取取消间接在可能的情况。  
  
```
void cancel();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。  
  
##  <a name="is_canceling"></a> is_canceling 

 通知调用方任务组当前正在取消操作。 这不一定表示的`cancel`上调用了方法`structured_task_group`对象 (尽管这样肯定会让此方法以返回`true`)。 它可能发生此情况的`structured_task_group`对象正在执行内联和任务组进一步向上工作树中已取消。 在这些位置等的情况下运行时可以确定取消将流过提前`structured_task_group`对象，`true`也将返回。  
  
```
bool is_canceling();
```  
  
### <a name="return-value"></a>返回值  
 指示是否`structured_task_group`对象是否正在取消操作 （或保证可稍后）。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。  
  
##  <a name="run"></a> 运行 

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
*_Function*<br/>
将调用以执行任务句柄的主体的函数对象的类型。  
  
*_Task_handle*<br/>
句柄正在计划的工作。 请注意，调用方负责此对象的生存期。 在运行时将继续期望其存留，直至`wait`或`run_and_wait`对此调用方法`structured_task_group`对象。  
  
*放置 （_p)*<br/>
对应执行 `_Task_handle` 参数所表示任务的位置的引用。  
  
### <a name="remarks"></a>备注  
 运行时创建一份工作函数传递给此方法。 将传递给此方法的函数对象中发生的任何状态更改不会在该函数对象的副本中。  
  
 如果`structured_task_group`因堆栈展开从异常的结果，您不需要保证，已调用为`wait`或`run_and_wait`方法。 在这种情况下，析构函数将相应地取消并等待由任务`_Task_handle`参数来完成。  
  
 将引发[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)如果该任务处理的异常由给定`_Task_handle`参数已安排到通过任务组对象上`run`方法并且已对任何干预调用要么`wait`或`run_and_wait`任务组上的方法。  
  
##  <a name="run_and_wait"></a> run_and_wait 

 计划任务以运行内联将在调用上下文的帮助下`structured_task_group`完整的取消支持的对象。 如果`task_handle`对象作为参数传递`run_and_wait`，调用方负责管理的生存期`task_handle`对象。 然后函数等待直到上的所有工作`structured_task_group`对象已完成或已取消。  
  
```
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```  
  
### <a name="parameters"></a>参数  
*_Function*<br/>
将调用以执行任务的函数对象的类型。  
  
*_Task_handle*<br/>
句柄将在调用上下文以内联方式运行的任务。 请注意，调用方负责此对象的生存期。 在运行时将继续期望其存留，直至`run_and_wait`方法完成执行。  
  
*_Func*<br/>
一个函数，它将调用以调用该工作的正文。 这可能是 lambda 或其他对象，支持具有签名的函数调用运算符的版本`void operator()()`。  
  
### <a name="return-value"></a>返回值  
 指示是否满足该等待或任务组已取消，因显式取消操作或从其任务之一所引发的异常。 有关详细信息，请参阅[task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>备注  
 请注意，其中一个或多个任务安排到`structured_task_group`对象可能会将在调用上下文中执行内联。  
  
 如果一个或多个与此计划的任务`structured_task_group`对象引发了异常，运行时将选择其选择的一个此类异常，并将其传播到调用`run_and_wait`方法。  
  
 返回此函数后，`structured_task_group` 对象被视为处于最终状态，并且不应使用。 请注意该之后的利用率`run_and_wait`方法返回将导致未定义的行为。  
  
 在执行非异常路径，具有一定要这样做来调用此方法或`wait`方法之前的析构函数`structured_task_group`执行。  
  
##  <a name="ctor"></a> structured_task_group 

 构造一个新`structured_task_group`对象。  
  
```
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```  
  
### <a name="parameters"></a>参数  
*_CancellationToken*<br/>
要将与此结构化的任务组相关联的取消标记。 标记被取消时，结构化的任务组将被取消。  
  
### <a name="remarks"></a>备注  
 采用取消标记的构造函数会创建一个在取消与标记相关联的源时将会取消的 `structured_task_group`。 提供显式取消标记也可以避免此结构化的任务组参与不同的标记或没有标记的父组的隐式取消。  
  
##  <a name="dtor"></a> ~structured_task_group 

 销毁 `structured_task_group` 对象。 你应该调用`wait`或`run_and_wait`之前析构函数执行的对象上的方法执行析构函数，除非为堆栈展开因异常而。  
  
```
~structured_task_group();
```  
  
### <a name="remarks"></a>备注  
 如果析构函数导致正常执行过程中 （例如，不堆栈展开由于出现异常） 以及既不运行`wait`也不`run_and_wait`在调用方法、 析构函数可能会引发[missing_wait](missing-wait-class.md)异常。  
  
##  <a name="wait"></a> 等待 

 等待，直到上的所有工作`structured_task_group`已完成或已取消。  
  
```
task_group_status wait();
```  
  
### <a name="return-value"></a>返回值  
 指示是否满足该等待或任务组已取消，因显式取消操作或从其任务之一所引发的异常。 有关详细信息，请参阅[task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>备注  
 请注意，其中一个或多个任务安排到`structured_task_group`对象可能会将在调用上下文中执行内联。  
  
 如果一个或多个与此计划的任务`structured_task_group`对象引发了异常，运行时将选择其选择的一个此类异常，并将其传播到调用`wait`方法。  
  
 返回此函数后，`structured_task_group` 对象被视为处于最终状态，并且不应使用。 请注意该之后的利用率`wait`方法返回将导致未定义的行为。  
  
 在执行非异常路径，具有一定要这样做来调用此方法或`run_and_wait`方法之前的析构函数`structured_task_group`执行。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [task_group 类](task-group-class.md)   
 [task_handle 类](task-handle-class.md)
