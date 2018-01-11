---
title: "event 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- event
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
dev_langs: C++
helpviewer_keywords: event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 550cbdda0468db969ffe3c7d3412789c1f0e5976
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="event-class"></a>event 类
明确感知并发运行时的手动重置事件。  
  
## <a name="syntax"></a>语法  
  
```
class event;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[~ event 析构函数](#dtor)|销毁事件。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[reset](#reset)|将事件重置为非终止状态。|  
|[set](#set)|用信号通知事件。|  
|[等待](#wait)|等待事件变为终止状态。|  
|[wait_for_multiple](#wait_for_multiple)|等待多个事件都变为终止状态。|  
  
### <a name="public-constants"></a>公共常量  
  
|name|描述|  
|----------|-----------------|  
|[timeout_infinite](#timeout_infinite)|指示等待永远不应超时的值。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `event`  
  
## <a name="requirements"></a>惠?  
 **标头：** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a>事件 

 构造一个新的事件。  
  
```
_CRTIMP event();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="dtor"></a>~ 事件 

 销毁事件。  
  
```
~event();
```  
  
### <a name="remarks"></a>备注  
 应在没有线程等待事件析构函数运行时。 在线程仍处于等待状态时允许析构事件会导致未定义的行为。  
  
##  <a name="reset"></a>重置 

 将事件重置为非终止状态。  
  
```
void reset();
```  
  
##  <a name="set"></a>设置 

 用信号通知事件。  
  
```
void set();
```  
  
### <a name="remarks"></a>备注  
 发出事件信号会导致等待该事件的任意数量的上下文变为可运行。  
  
##  <a name="timeout_infinite"></a>timeout_infinite 

 指示等待永远不应超时的值。  
  
```
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```  
  
##  <a name="wait"></a>等待 

 等待事件变为终止状态。  
  
```
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>参数  
 `_Timeout`  
 在等待超时之前，请指示毫秒的数。值`COOPERATIVE_TIMEOUT_INFINITE`表示无超时。  
  
### <a name="return-value"></a>返回值  
 如果未满足等待，值`0`返回; 否则为值`COOPERATIVE_WAIT_TIMEOUT`以指示等待操作超时而无需成为发出信号的事件。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)] 应用程序中，不要对 ASTA 线程调用 `wait`，因为该调用会阻塞当前线程并且会导致应用程序不响应。  
  
##  <a name="wait_for_multiple"></a>wait_for_multiple 

 等待多个事件都变为终止状态。  
  
```
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>参数  
 `_PPEvents`  
 要等待的事件的数组。 在该数组中的事件数将由`count`参数。  
  
 `count`  
 中提供该数组中的事件的计数`_PPEvents`参数。  
  
 `_FWaitAll`  
 如果设置为值`true`，参数指定在该数组中的所有事件中都提供`_PPEvents`参数必须以满足等待变为终止状态。 如果设置为值`false`，它指定在该数组中的任何事件中提供`_PPEvents`变得有信号状态的参数将满足等待。  
  
 `_Timeout`  
 在等待超时之前，请指示毫秒的数。值`COOPERATIVE_TIMEOUT_INFINITE`表示无超时。  
  
### <a name="return-value"></a>返回值  
 如果未满足等待，在该数组中的索引中提供`_PPEvents`参数它满足等待条件中; 否则为值`COOPERATIVE_WAIT_TIMEOUT`以指示等待操作超时而无需满足该条件时。  
  
### <a name="remarks"></a>备注  
 如果参数`_FWaitAll`设置为值`true`以指示所有事件必须成为都终止才能满足等待，函数返回的索引没有任何特殊意义它不是值的事实之外`COOPERATIVE_WAIT_TIMEOUT`。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)] 应用程序中，不要对 ASTA 线程调用 `wait_for_multiple`，因为该调用会阻塞当前线程并且会导致应用程序不响应。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
