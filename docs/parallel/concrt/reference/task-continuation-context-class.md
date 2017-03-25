---
title: "task_continuation_context 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 8afd599e5ee489500d7f8c498d03c91ace6b99ed
ms.lasthandoff: 03/17/2017

---
# <a name="taskcontinuationcontext-class"></a>task_continuation_context 类
`task_continuation_context` 类可让你指定想要执行延续的位置。 只能从 Windows 应用商店应用使用此类。 对于非 Windows 应用商店应用，任务延续的执行上下文由运行时确定，不可配置。  
  
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
  
## <a name="requirements"></a>要求  
 **标头︰** ppltasks.h  
  
 **命名空间：** 并发  

## <a name="get_current_winrt_context"></a>get_current_winrt_context
 返回表示当前的 WinRT 线程上下文的任务延续上下文对象。  
  
## <a name="syntax"></a>语法  
  
```  
static task_continuation_context get_current_winrt_context();  
```  
  
## <a name="return-value"></a>返回值  
 当前的 Windows 运行时线程上下文。 如果从非 Windows 运行时上下文中调用，则返回空 task_continuation_context。  
  
## <a name="remarks"></a>备注  
 `get_current_winrt_context`方法捕获调用方的 Windows 运行时线程上下文。 它对非 Windows 运行时调用方返回一个空的上下文。  
  
 返回的值`get_current_winrt_context`可以用于指示向运行时，应执行延续在捕获的上下文 (STA vs 为 MTA) 的单元模型中，无论在前面的任务是否感知的单元。 注意任务是解包 Windows 运行时的任务单元`IAsyncInfo`接口或源于此类任务的任务。  
  
 此方法类似于是`use_current`方法，但它也是可用于本机 c + + 代码不使用 C + + /cli CX 扩展支持。 适用于在使用高级用户编写 C + + /cli CX 不可知本机模式和 Windows 运行时调用方的库代码。 除非您需要此功能，否则我们建议`use_current`方法，仅可供 C + + /cli CX 客户端。  
  
  
##  <a name="use_arbitrary"></a>use_arbitrary 

 创建允许运行时选择延续的执行上下文的任务延续上下文。  
  
```
static task_continuation_context use_arbitrary();
```  
  
### <a name="return-value"></a>返回值  
 一个表示的任意位置的任务延续上下文。  
  
### <a name="remarks"></a>备注  
 使用此延续上下文时将则运行时会选择即使在前面的任务是单元感知上下文中执行延续任务。  
  
 `use_arbitrary`可用于关闭在单元注意任务在 STA 中创建的延续任务的默认行为  
  
 此方法仅适用于 Windows 应用商店应用。  
  
##  <a name="use_current"></a>use_current 

 返回表示当前执行上下文的任务延续上下文对象。  
  
```
static task_continuation_context use_current();
```  
  
### <a name="return-value"></a>返回值  
 当前执行上下文。  
  
### <a name="remarks"></a>备注  
 此方法，以便可以在右侧的单元内执行时间延续任务捕获调用方的 Windows 运行时上下文。  
  
 返回的值`use_current`可以用于向运行时指示执行延续的而不考虑是否在前面的任务是单元感知捕获的上下文 (STA vs MTA) 中。 注意任务是解包 Windows 运行时的任务单元`IAsyncInfo`接口或源于此类任务的任务。  
  
 此方法仅适用于 Windows 应用商店应用。  
  
##  <a name="use_default"></a>use_default 

 创建默认任务延续上下文。  
  
```
static task_continuation_context use_default();
```  
  
### <a name="return-value"></a>返回值  
 默认延续上下文。  
  
### <a name="remarks"></a>备注  
 如果未指定延续上下文调用时，则使用默认上下文`then`方法。 在 Windows 应用程序适用于 Windows 7 和下方，以及桌面应用程序在 Windows 8 和更高版本，运行时确定任务延续将在其中执行。 但是，在 Windows 应用商店应用中，在单元感知任务的延续任务的默认延续上下文是单元其中`then`调用。  
  
 注意任务是解包 Windows 运行时的任务单元`IAsyncInfo`接口或源于此类任务的任务。 因此，如果您计划对在 Windows 运行时 STA 单元注意任务的延续任务，则延续任务将执行在该 sta。  
  
 非单元注意任务将在运行时选择的上下文中执行。  

## <a name="use_synchronous_execution"></a>task_continuation_context::use_synchronous_execution  
返回表示执行同步上下文的任务延续上下文对象。  
  
## <a name="syntax"></a>语法  
  
```  
static task_continuation_context use_synchronous_execution();  
```  
  
## <a name="return-value"></a>返回值  
 执行同步上下文中。  
  
## <a name="remarks"></a>备注  
 `use_synchronous_execution`方法强制延续任务在上下文中，从而导致其前面的任务完成同步运行。  
  
 如果在前面的任务已完成时将延续附加，则延续任务同步运行延续任务会将附加的上下文。  
  
 
## <a name="see-also"></a>另请参阅  
 [并发命名空间](concurrency-namespace.md)

