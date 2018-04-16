---
title: "agent 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- agent
- AGENTS/concurrency::agent
- AGENTS/concurrency::agent::agent
- AGENTS/concurrency::agent::cancel
- AGENTS/concurrency::agent::start
- AGENTS/concurrency::agent::status
- AGENTS/concurrency::agent::status_port
- AGENTS/concurrency::agent::wait
- AGENTS/concurrency::agent::wait_for_all
- AGENTS/concurrency::agent::wait_for_one
- AGENTS/concurrency::agent::done
- AGENTS/concurrency::agent::run
dev_langs:
- C++
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a4617007525fdd924dce7b09f1d351c7c18cc96
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="agent-class"></a>agent 类
旨在用作所有独立代理的基类的类。 用于对其他代理隐藏状态并通过消息传递进行交互。  
  
## <a name="syntax"></a>语法  
  
```
class agent;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[agent](#ctor)|已重载。 构造一个代理。|  
|[~ agent 析构函数](#dtor)|销毁代理。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[cancel](#cancel)|将代理移从`agent_created`或`agent_runnable`状态到`agent_canceled`状态。|  
|[start](#start)|将从代理移`agent_created`状态`agent_runnable`状态，并且计划执行。|  
|[status](#status)|从代理的状态信息的同步源。|  
|[status_port](#status_port)|从代理的状态信息的一种异步来源。|  
|[wait](#wait)|等待代理为了完成其任务。|  
|[wait_for_all](#wait_for_all)|等待所有指定的代理来完成其任务。|  
|[wait_for_one](#wait_for_one)|等待任何一种指定的代理，为了完成其任务。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[done](#done)|将移动到代理`agent_done`状态，指示该代理已完成。|  
|[run](#run)|表示代理的主要任务。 `run` 应在派生类中重写，并指定代理应执行的操作已启动。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[异步代理](../../../parallel/concrt/asynchronous-agents.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `agent`  
  
## <a name="requirements"></a>惠?  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="ctor"></a> 代理 

 构造一个代理。  
  
```
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```  
  
### <a name="parameters"></a>参数  
 `_PScheduler`  
 `Scheduler`对象内执行任务的代理计划。  
  
 `_PGroup`  
 `ScheduleGroup`对象内执行任务的代理计划。 所用 `Scheduler` 对象由该计划组提示。  
  
### <a name="remarks"></a>备注  
 如果未指定，运行时将使用默认计划程序`_PScheduler`或`_PGroup`参数。  
  
##  <a name="dtor"></a> ~ 代理 

 销毁代理。  
  
```
virtual ~agent();
```  
  
### <a name="remarks"></a>备注  
 它是错误销毁不处于终止状态的代理 (请`agent_done`或`agent_canceled`)。 通过等待代理到达终止状态的析构函数中的继承自的类，这可以避免`agent`类。  
  
##  <a name="cancel"></a> 取消 

 将代理移从`agent_created`或`agent_runnable`状态到`agent_canceled`状态。  
  
```
bool cancel();
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果代理已取消，`false`否则为。 无法取消代理，如果它已经启动了运行或已完成。  
  
##  <a name="done"></a> 完成 

 将移动到代理`agent_done`状态，指示该代理已完成。  
  
```
bool done();
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果代理移动到`agent_done`状态，`false`否则为。 已取消的代理不能移到`agent_done`状态。  
  
### <a name="remarks"></a>备注  
 应该在末尾调用此方法`run`方法，当你知道你的代理执行时完成。  
  
##  <a name="run"></a> run 

 表示代理的主要任务。 `run` 应在派生类中重写，并指定代理应执行的操作已启动。  
  
```
virtual void run() = 0;
```  
  
### <a name="remarks"></a>备注  
 代理状态将更改为`agent_started`右键之前调用此方法。 该方法应调用`done`的代理上的相应的状态之前返回，并且可能不会引发任何异常。  
  
##  <a name="start"></a> 启动 

 将从代理移`agent_created`状态`agent_runnable`状态，并且计划执行。  
  
```
bool start();
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果正确，启动代理`false`否则为。 已取消的代理无法启动。  
  
##  <a name="status"></a> 状态 

 从代理的状态信息的同步源。  
  
```
agent_status status();
```  
  
### <a name="return-value"></a>返回值  
 返回的代理的当前状态。 请注意，在返回后立即中无法更改此返回的状态。  
  
##  <a name="status_port"></a> status_port 

 从代理的状态信息的一种异步来源。  
  
```
ISource<agent_status>* status_port();
```  
  
### <a name="return-value"></a>返回值  
 返回可以发送有关代理的当前状态的消息的消息源。  
  
##  <a name="wait"></a> 等待 

 等待代理为了完成其任务。  
  
```
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>参数  
 `_PAgent`  
 指向要等待的时间的代理的指针。  
  
 `_Timeout`  
 若要等待，以毫秒为单位最长时间。  
  
### <a name="return-value"></a>返回值  
 `agent_status`等待完成时的代理。 这可能是`agent_canceled`或`agent_done`。  
  
### <a name="remarks"></a>备注  
 代理任务完成时代理进入`agent_canceled`或`agent_done`状态。  
  
 如果参数`_Timeout`具有常量以外的值`COOPERATIVE_TIMEOUT_INFINITE`，异常[operation_timed_out](operation-timed-out-class.md)如果指定的时间量过期代理完成其任务之前，将引发。  
  
##  <a name="wait_for_all"></a> wait_for_all 

 等待所有指定的代理来完成其任务。  
  
```
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>参数  
 `count`  
 数组中出现代理指针数目`_PAgents`。  
  
 `_PAgents`  
 指向要等待的时间的代理的指针的数组。  
  
 `_PStatus`  
 指向代理状态的数组的指针。 此方法返回时，每个状态值将表示相应的代理的状态。  
  
 `_Timeout`  
 若要等待，以毫秒为单位最长时间。  
  
### <a name="remarks"></a>备注  
 代理任务完成时代理进入`agent_canceled`或`agent_done`状态。  
  
 如果参数`_Timeout`具有常量以外的值`COOPERATIVE_TIMEOUT_INFINITE`，异常[operation_timed_out](operation-timed-out-class.md)如果指定的时间量过期代理完成其任务之前，将引发。  
  
##  <a name="wait_for_one"></a> wait_for_one 

 等待任何一种指定的代理，为了完成其任务。  
  
```
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>参数  
 `count`  
 数组中出现代理指针数目`_PAgents`。  
  
 `_PAgents`  
 指向要等待的时间的代理的指针的数组。  
  
 `_Status`  
 对在其中放置的代理状态的变量的引用。  
  
 `_Index`  
 对在其中放置的代理索引变量的引用。  
  
 `_Timeout`  
 若要等待，以毫秒为单位最长时间。  
  
### <a name="remarks"></a>备注  
 代理任务完成时代理进入`agent_canceled`或`agent_done`状态。  
  
 如果参数`_Timeout`具有常量以外的值`COOPERATIVE_TIMEOUT_INFINITE`，异常[operation_timed_out](operation-timed-out-class.md)如果指定的时间量过期代理完成其任务之前，将引发。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
