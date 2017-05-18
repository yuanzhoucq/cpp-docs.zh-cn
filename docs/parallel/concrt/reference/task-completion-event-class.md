---
title: "task_completion_event 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- task_completion_event
- PPLTASKS/concurrency::task_completion_event
- PPLTASKS/concurrency::task_completion_event::task_completion_event
- PPLTASKS/concurrency::task_completion_event::set
- PPLTASKS/concurrency::task_completion_event::set_exception
dev_langs:
- C++
helpviewer_keywords:
- task_completion_event class
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
caps.latest.revision: 11
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: b37ecb250c0794370fc586f0463f93023ca47603
ms.contentlocale: zh-cn
ms.lasthandoff: 03/17/2017

---
# <a name="taskcompletionevent-class"></a>task_completion_event 类
`task_completion_event` 类可让你延迟任务的执行，直到满足条件，或开始一项任务来响应外部事件。  
  
## <a name="syntax"></a>语法  
  
```
template<typename _ResultType>
class task_completion_event;

template<>
class task_completion_event<void>;
```  
  
#### <a name="parameters"></a>参数  
 `_ResultType`  
 此 `task_completion_event` 类的结果类型。  
  
 `T`  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[task_completion_event](#ctor)|构造 `task_completion_event` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[set](#set)|已重载。 设置任务完成事件。|  
|[set_exception](#set_exception)|已重载。 传播与此事件关联的所有任务的一个例外情况。|  
  
## <a name="remarks"></a>备注  
 在你的方案要求创建将完成的任务时使用基于任务完成事件创建的任务，从而计划在将来的某个时候执行其延续。 `task_completion_event` 的类型必须与创建的任务的类型相同，而对包含该类型的值的任务完成事件调用 set 方法将导致关联的任务完成，并提供该值作为其延续的结果。  
  
 如果任务完成事件始终未收到信号，则当它被销毁时，基于它创建的任何任务都将被取消。  
  
 `task_completion_event` 的行为类似于能指针，并应按值传递。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `task_completion_event`  
  
## <a name="requirements"></a>要求  
 **标头︰** ppltasks.h  
  
 **命名空间：** 并发  
  
##  <a name="set"></a>设置 

 设置任务完成事件。  
  
```
bool set(_ResultType _Result) const ;

bool set() const ;
```  
  
### <a name="parameters"></a>参数  
 `_Result`  
 要设置与此事件的结果。  
  
### <a name="return-value"></a>返回值  
 该方法返回`true`是否成功地设置该事件。 它将返回`false`如果已经设置了事件。  
  
### <a name="remarks"></a>备注  
 在多个存在或对并发调用`set`，仅第一次调用将失败，并且其结果 （如果有） 将存储在任务完成事件。 剩余的集将被忽略并且该方法将返回 false。 如果设置任务完成事件时，所有任务从都创建的事件将立即完成，并且其延续，如果有的话，这将安排。 任务已完成对象`_ResultType`以外`void`将的值传递给它们的延续。  
  
##  <a name="set_exception"></a>set_exception 

 传播与此事件关联的所有任务的一个例外情况。  
  
```
template<typename _E>
__declspec(noinline) bool set_exception(_E _Except) const;

__declspec(noinline) bool set_exception(std::exception_ptr _ExceptionPtr) const ;
```  
  
### <a name="parameters"></a>参数  
 `_E`  
 `_Except`  
 `_ExceptionPtr`  
  
### <a name="return-value"></a>返回值  
  
##  <a name="ctor"></a>task_completion_event 

 构造 `task_completion_event` 对象。  
  
```
task_completion_event();
```  
  
## <a name="see-also"></a>另请参阅  
 [并发命名空间](concurrency-namespace.md)

