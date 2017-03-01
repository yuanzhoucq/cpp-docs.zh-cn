---
title: "event 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::event
dev_langs:
- C++
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
caps.latest.revision: 22
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
ms.openlocfilehash: abda6512f391b59cb48c8e96a489714ee117ae68
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[reset 方法](#reset)|为非终止状态重置事件。|  
|[set 方法](#set)|用信号通知事件。|  
|[wait 方法](#wait)|等待要接收信号的事件。|  
|[wait_for_multiple 方法](#wait_for_multiple)|等待多个事件都变为终止状态。|  
  
### <a name="public-constants"></a>公共常量  
  
|名称|说明|  
|----------|-----------------|  
|[timeout_infinite 常量](#timeout_infinite)|指示等待永远不应超时的值。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `event`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namectora-event"></a><a name="ctor"></a>事件 

 构造一个新的事件。  
  
```
_CRTIMP event();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namedtora-event"></a><a name="dtor"></a>~ 事件 

 销毁事件。  
  
```
~event();
```  
  
### <a name="remarks"></a>备注  
 预计有没有线程正在等待析构函数运行时的事件。 在线程仍处于等待状态时允许析构事件会导致未定义的行为。  
  
##  <a name="a-namereseta-reset"></a><a name="reset"></a>重置 

 为非终止状态重置事件。  
  
```
void reset();
```  
  
##  <a name="a-nameseta-set"></a><a name="set"></a>设置 

 用信号通知事件。  
  
```
void set();
```  
  
### <a name="remarks"></a>备注  
 发出事件信号会导致等待该事件的任意数量的上下文变为可运行。  
  
##  <a name="a-nametimeoutinfinitea-timeoutinfinite"></a><a name="timeout_infinite"></a>timeout_infinite 

 指示等待永远不应超时的值。  
  
```
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```  
  
##  <a name="a-namewaita-wait"></a><a name="wait"></a>等待 

 等待要接收信号的事件。  
  
```
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>参数  
 `_Timeout`  
 表示毫秒的数之前等待超时。 值`COOPERATIVE_TIMEOUT_INFINITE`表示无超时。  
  
### <a name="return-value"></a>返回值  
 如果满足该等待，则这`0`返回; 否则为值`COOPERATIVE_WAIT_TIMEOUT`以指示在等待而无需成为发出信号的事件已超时。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)] 应用程序中，不要对 ASTA 线程调用 `wait`，因为该调用会阻塞当前线程并且会导致应用程序不响应。  
  
##  <a name="a-namewaitformultiplea-waitformultiple"></a><a name="wait_for_multiple"></a>wait_for_multiple 

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
 要等待的事件数组。 在该数组中的事件数由`count`参数。  
  
 `count`  
 中提供的数组内的事件数`_PPEvents`参数。  
  
 `_FWaitAll`  
 如果设置为值`true`，该参数指定在该数组中的所有事件中都提供`_PPEvents`参数必须以满足在等待接收信号。 如果设置为值`false`，它指定在该数组中的任何事件中提供`_PPEvents`变为终止状态的参数将满足等待。  
  
 `_Timeout`  
 表示毫秒的数之前等待超时。 值`COOPERATIVE_TIMEOUT_INFINITE`表示无超时。  
  
### <a name="return-value"></a>返回值  
 如果满足该等待，在该数组中的索引中提供`_PPEvents`参数它满足等待的条件; 否则为值`COOPERATIVE_WAIT_TIMEOUT`以指示在等待不满足该条件时的情况下已超时。  
  
### <a name="remarks"></a>备注  
 如果该参数`_FWaitAll`设置为值`true`若要指示所有事件必须成为都信号才能满足等待，由该函数返回的索引没有任何特殊意义它不是值的事实之外`COOPERATIVE_WAIT_TIMEOUT`。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)] 应用程序中，不要对 ASTA 线程调用 `wait_for_multiple`，因为该调用会阻塞当前线程并且会导致应用程序不响应。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

