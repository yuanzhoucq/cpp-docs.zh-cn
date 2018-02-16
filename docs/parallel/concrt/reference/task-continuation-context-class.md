---
title: "task_continuation_context 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
dev_langs:
- C++
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b78688493bbb8d8bdad0696a7c8fcf467519000
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="taskcontinuationcontext-class"></a>task_continuation_context 类
`task_continuation_context` 类可让你指定想要执行延续的位置。 最好仅使用从 Windows 运行时应用此类。 对于非 Windows 运行时应用程序，任务延续的执行上下文是由运行时，并且不可配置。  
  
## <a name="syntax"></a>语法  
  
```
class task_continuation_context : public details::_ContextCallback;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[get_current_winrt_context](#get_current_winrt_context)|返回表示当前的 winrt 线程上下文的任务延续上下文对象。|  
|[use_arbitrary](#use_arbitrary)|创建允许运行时选择延续的执行上下文的任务延续上下文。|  
|[use_current](#use_current)|返回表示当前执行上下文的任务延续上下文对象。|  
|[use_default](#use_default)|创建默认任务延续上下文。|  
|[use_synchronous_execution](#use_synchronous_execution)|返回表示执行同步上下文的任务延续上下文对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `_ContextCallback`  
  
 `task_continuation_context`  
  
## <a name="requirements"></a>惠?  
 **标头：** ppltasks.h  
  
 **命名空间：** 并发  

## <a name="get_current_winrt_context"></a> get_current_winrt_context
 返回表示当前的 WinRT 线程上下文的任务延续上下文对象。  
  
## <a name="syntax"></a>语法  
  
```  
static task_continuation_context get_current_winrt_context();  
```  
  
## <a name="return-value"></a>返回值  
 当前的 Windows 运行时线程上下文。 如果从非 Windows 运行时上下文中调用，则返回空 task_continuation_context。  
  
## <a name="remarks"></a>备注  
 `get_current_winrt_context`方法捕获调用方的 Windows 运行时线程上下文。 它向非 Windows 运行时调用方返回一个空的上下文。  
  
 返回的值`get_current_winrt_context`可以用于向运行时，执行延续的在捕获的上下文 (STA vs 为 MTA) 的单元模型中，无论前面的任务是否单元感知的指示。 注意任务是解包 Windows 运行时的任务单元`IAsyncInfo`接口或从这种任务继承的任务。  
  
 此方法类似于是`use_current`方法，但它也是可用于本机 c + + 代码，而无需 C + + /cli CX 扩展支持。 适用于在通过使用高级用户编写 C + + /cli CX 无关对于本机模式和 Windows 运行时调用方的库代码。 除非你需要此功能，否则我们建议`use_current`方法，仅可供 C + + /cli CX 客户端。  
  
  
##  <a name="use_arbitrary"></a> use_arbitrary 

 创建允许运行时选择延续的执行上下文的任务延续上下文。  
  
```
static task_continuation_context use_arbitrary();
```  
  
### <a name="return-value"></a>返回值  
 表示的任意位置的任务延续上下文。  
  
### <a name="remarks"></a>备注  
 使用此延续上下文时则运行时会选择即使前面的任务是单元感知上下文中将执行延续。  
  
 `use_arbitrary` 可用于关闭在 STA 中创建一个单元感知任务的延续任务的默认行为  
  
 此方法仅可用于 Windows 运行时应用。  
  
##  <a name="use_current"></a> use_current 

 返回表示当前执行上下文的任务延续上下文对象。  
  
```
static task_continuation_context use_current();
```  
  
### <a name="return-value"></a>返回值  
 当前执行上下文。  
  
### <a name="remarks"></a>备注  
 此方法，以便可以在右侧的单元中执行延续捕获调用方的 Windows 运行时上下文。  
  
 返回的值`use_current`可以用于指示为运行时执行延续的无论前面的任务是否为单元感知的捕获上下文 (STA vs MTA) 中。 注意任务是解包 Windows 运行时的任务单元`IAsyncInfo`接口或从这种任务继承的任务。  
  
 此方法仅可用于 Windows 运行时应用。  
  
##  <a name="use_default"></a> use_default 

 创建默认任务延续上下文。  
  
```
static task_continuation_context use_default();
```  
  
### <a name="return-value"></a>返回值  
 默认延续上下文。  
  
### <a name="remarks"></a>备注  
 如果未指定延续上下文在调用时，则使用默认上下文`then`方法。 对于 Windows 7 和下面的 Windows 应用程序以及桌面应用程序在 Windows 8 和更高版本，在运行时确定任务延续将在其中执行。 但是，在 Windows 运行时应用中，单元感知任务的延续的默认延续上下文是单元其中`then`调用。  
  
 注意任务是解包 Windows 运行时的任务单元`IAsyncInfo`接口或从这种任务继承的任务。 因此，如果您计划在 Windows 运行时 STA 单元感知任务的延续任务时，延续将执行在该 sta。  
  
 非单元感知任务的延续任务将在运行时会选择某个上下文中执行。  

## <a name="use_synchronous_execution"></a> task_continuation_context::use_synchronous_execution  
返回表示执行同步上下文的任务延续上下文对象。  
  
## <a name="syntax"></a>语法  
  
```  
static task_continuation_context use_synchronous_execution();  
```  
  
## <a name="return-value"></a>返回值  
 执行同步上下文中。  
  
## <a name="remarks"></a>备注  
 `use_synchronous_execution`方法强制为上下文，导致其前面的任务完成异步运行延续任务。  
  
 如果先行任务已完成时将延续附加，延续运行以同步方式将延续附加上下文。  
  
 
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
