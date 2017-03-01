---
title: "structured_task_group 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ppl/concurrency::structured_task_group
dev_langs:
- C++
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: ef20ff7fef8683cec4a3856c80c09846aa69a89a
ms.lasthandoff: 02/24/2017

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
|[structured_task_group 构造函数](#ctor)|已重载。 构造一个新`structured_task_group`对象。|  
|[~ structured_task_group 析构函数](#dtor)|销毁 `structured_task_group` 对象。 您应调用`wait`或`run_and_wait`之前析构函数执行的对象上的方法除非执行析构函数引发的堆栈展开由于出现异常。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[cancel 方法](#cancel)|使最大努力以尝试取消工作为根的此任务组的子树。 对任务组计划每个任务都将获取取消间接如有可能。|  
|[is_canceling 方法](#is_canceling)|任务组当前正在取消通知调用方。 这不一定表示，`cancel`上调用方法`structured_task_group`对象 (尽管这样肯定会让此方法以返回`true`)。 它可能出现此情况，`structured_task_group`对象正在执行内联，任务组进一步向上工作树中已被取消。 在这些位置等的情况下运行时可以提前确定取消将流过`structured_task_group`对象，`true`也会返回。|  
|[run 的方法](#run)|已重载。 在计划任务`structured_task_group`对象。 调用方管理的生存期`task_handle`传入的对象`_Task_handle`参数。 采用参数 `_Placement` 的版本会导致任务偏向在该参数指定的位置执行。|  
|[run_and_wait 方法](#run_and_wait)|已重载。 计划任务运行内联来在调用上下文的帮助下`structured_task_group`完全取消支持的对象。 如果`task_handle`对象作为参数传递给`run_and_wait`，调用方负责管理的生存期`task_handle`对象。 函数等待直到上的所有工作`structured_task_group`对象已完成或已取消。|  
|[wait 方法](#wait)|一直等待，直到上的所有工作`structured_task_group`已完成或被取消。|  
  
## <a name="remarks"></a>备注  
 有许多严格限制的使用情况`structured_task_group`对象以便获得的性能︰  
  
-   单个`structured_task_group`对象不能由多个线程。 上的所有操作`structured_task_group`对象必须由创建该对象的线程执行。 此规则的两个例外是成员函数`cancel`和`is_canceling`。 该对象可能不是 lambda 表达式的捕获列表中，并且除非任务占用了取消操作的其中一个任务中使用。  
  
-   所有任务计划为`structured_task_group`对象计划使用`task_handle`对象必须显式管理的生存期。  
  
-   中绝对嵌套顺序，只可能使用多个组。 如果两个`structured_task_group`声明对象，第二个要声明 （内部一） 必须在除任何其他方法之前析构`cancel`或`is_canceling`上的第一个调用 （外部一个）。 此条件成立在这两种情况下声明多个`structured_task_group`相同或功能嵌套作用域，以及任务排队到这种情况中的对象`structured_task_group`通过`run`或`run_and_wait`方法。  
  
-   与常规不同`task_group`类中的所有状态`structured_task_group`都类是最终版。 已将任务排队到组并等待它们完成后，你可能不会再次使用同一个组。  
  
 有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `structured_task_group`  
  
## <a name="requirements"></a>要求  
 **标头︰** ppl.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namecancela-cancel"></a><a name="cancel"></a>取消 

 使最大努力以尝试取消工作为根的此任务组的子树。 对任务组计划每个任务都将获取取消间接如有可能。  
  
```
void cancel();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。  
  
##  <a name="a-nameiscancelinga-iscanceling"></a><a name="is_canceling"></a>is_canceling 

 任务组当前正在取消通知调用方。 这不一定表示，`cancel`上调用方法`structured_task_group`对象 (尽管这样肯定会让此方法以返回`true`)。 它可能出现此情况，`structured_task_group`对象正在执行内联，任务组进一步向上工作树中已被取消。 在这些位置等的情况下运行时可以提前确定取消将流过`structured_task_group`对象，`true`也会返回。  
  
```
bool is_canceling();
```  
  
### <a name="return-value"></a>返回值  
 指示是否`structured_task_group`对象是否正在取消 （或保证很快被）。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。  
  
##  <a name="a-nameruna-run"></a><a name="run"></a>运行 

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
 正在计划的工作句柄。 请注意，调用方负责此对象的生存期。 运行时将继续期望其存留，直至`wait`或`run_and_wait`方法调用此`structured_task_group`对象。  
  
 `_Placement`  
 对应执行 `_Task_handle` 参数所表示任务的位置的引用。  
  
### <a name="remarks"></a>备注  
 运行时创建的副本传递给此方法的工作函数。 传递给此方法的函数对象中发生的任何状态更改不会出现在该函数对象的副本。  
  
 如果`structured_task_group`因产生的异常从展开的堆栈，则您不需要确保调用已经进行到任一`wait`或`run_and_wait`方法。 在这种情况下，析构函数将相应地取消并等待由任务`_Task_handle`参数来完成。  
  
 引发[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)如果该任务处理的异常所提供的`_Task_handle`参数已被调度到任务组对象通过`run`方法并且已经没有中间调用`wait`或`run_and_wait`针对该任务组的方法。  
  
##  <a name="a-namerunandwaita-runandwait"></a><a name="run_and_wait"></a>run_and_wait 

 计划任务运行内联来在调用上下文的帮助下`structured_task_group`完全取消支持的对象。 如果`task_handle`对象作为参数传递给`run_and_wait`，调用方负责管理的生存期`task_handle`对象。 函数等待直到上的所有工作`structured_task_group`对象已完成或已取消。  
  
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
 将在调用上下文以内联方式运行的任务句柄。 请注意，调用方负责此对象的生存期。 运行时将继续期望其存留，直至`run_and_wait`方法完成执行。  
  
 `_Func`  
 一个函数，将调用以调用该工作的正文。 这可能是 lambda 或其他对象，支持具有签名的函数调用运算符的版本`void operator()()`。  
  
### <a name="return-value"></a>返回值  
 相对值的指示是否在等待是否符合要求或任务组已被取消，由于显式的取消操作或从其任务之一会引发异常。 有关详细信息，请参阅[task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>备注  
 请注意，其中一个或多个任务安排到`structured_task_group`对象可能会在调用上下文中执行内联。  
  
 如果一个或多个任务安排到`structured_task_group`对象引发了异常，则运行时将选择其选择的此类异常之一，并将其传播到调用`run_and_wait`方法。  
  
 返回此函数后，`structured_task_group` 对象被视为处于最终状态，并且不应使用。 请注意该之后的利用率`run_and_wait`方法返回时将导致未定义的行为。  
  
 在非异常的执行路径，您必须调用此方法的强制性要求或`wait`方法之前的析构函数`structured_task_group`执行。  
  
##  <a name="a-namectora-structuredtaskgroup"></a><a name="ctor"></a>structured_task_group 

 构造一个新`structured_task_group`对象。  
  
```
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```  
  
### <a name="parameters"></a>参数  
 `_CancellationToken`  
 与此结构化的任务组相关联的取消标记。 取消标记时，结构化的任务组将被取消。  
  
### <a name="remarks"></a>备注  
 采用取消标记的构造函数会创建一个在取消与标记相关联的源时将会取消的 `structured_task_group`。 提供显式取消标记也可以避免此结构化的任务组参与采用不同标记或没有标记的父组的隐式取消。  
  
##  <a name="a-namedtora-structuredtaskgroup"></a><a name="dtor"></a>~ structured_task_group 

 销毁 `structured_task_group` 对象。 您应调用`wait`或`run_and_wait`之前析构函数执行的对象上的方法除非执行析构函数引发的堆栈展开由于出现异常。  
  
```
~structured_task_group();
```  
  
### <a name="remarks"></a>备注  
 如果析构函数作为正常执行过程中 （例如，不堆栈展开由于异常） 且结果运行`wait`，也不`run_and_wait`在调用方法，析构函数可能会引发[missing_wait](missing-wait-class.md)异常。  
  
##  <a name="a-namewaita-wait"></a><a name="wait"></a>等待 

 一直等待，直到上的所有工作`structured_task_group`已完成或被取消。  
  
```
task_group_status wait();
```  
  
### <a name="return-value"></a>返回值  
 相对值的指示是否在等待是否符合要求或任务组已被取消，由于显式的取消操作或从其任务之一会引发异常。 有关详细信息，请参阅[task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>备注  
 请注意，其中一个或多个任务安排到`structured_task_group`对象可能会在调用上下文中执行内联。  
  
 如果一个或多个任务安排到`structured_task_group`对象引发了异常，则运行时将选择其选择的此类异常之一，并将其传播到调用`wait`方法。  
  
 返回此函数后，`structured_task_group` 对象被视为处于最终状态，并且不应使用。 请注意该之后的利用率`wait`方法返回时将导致未定义的行为。  
  
 在非异常的执行路径，您必须调用此方法的强制性要求或`run_and_wait`方法之前的析构函数`structured_task_group`执行。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [task_group 类](task-group-class.md)   
 [task_handle 类](task-handle-class.md)

