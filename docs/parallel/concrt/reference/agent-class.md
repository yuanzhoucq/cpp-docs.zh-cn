---
title: "agent 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::agent
dev_langs:
- C++
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
caps.latest.revision: 20
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 640e1d66a879e8eb73428b50339d6a325cfd7cb2
ms.lasthandoff: 02/24/2017

---
# <a name="agent-class"></a>agent 类
旨在用作所有独立代理的基类的类。 用于对其他代理隐藏状态并通过消息传递进行交互。  
  
## <a name="syntax"></a>语法  
  
```
class agent;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[代理构造函数](#ctor)|已重载。 构造一个代理。|  
|[~ agent 析构函数](#dtor)|销毁代理。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[cancel 方法](#cancel)|将代理移从`agent_created`或`agent_runnable`状态到`agent_canceled`状态。|  
|[start 方法](#start)|将从代理移`agent_created`状态进入`agent_runnable`状态，并且执行对其进行安排。|  
|[状态方法](#status)|来自代理的状态信息的同步源。|  
|[status_port 方法](#status_port)|来自代理的状态信息异步源。|  
|[wait 方法](#wait)|等待代理完成其任务。|  
|[wait_for_all 方法](#wait_for_all)|等待所有指定的代理来完成其任务。|  
|[wait_for_one 方法](#wait_for_one)|等待指定的代理完成其任务之一。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[done 的方法](#done)|将移动到代理`agent_done`状态，指示该代理已完成。|  
|[run 的方法](#run)|表示代理的主要任务。 `run`应在派生类中重写，并指定代理应执行的操作已启动。|  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[异步代理](../../../parallel/concrt/asynchronous-agents.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `agent`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namectora-agent"></a><a name="ctor"></a>代理 

 构造一个代理。  
  
```
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```  
  
### <a name="parameters"></a>参数  
 `_PScheduler`  
 `Scheduler`对象，在计划的执行任务的代理。  
  
 `_PGroup`  
 `ScheduleGroup`对象，在计划的执行任务的代理。 所用 `Scheduler` 对象由该计划组提示。  
  
### <a name="remarks"></a>备注  
 如果未指定，则运行时将使用默认计划程序`_PScheduler`或`_PGroup`参数。  
  
##  <a name="a-namedtora-agent"></a><a name="dtor"></a>~ 代理 

 销毁代理。  
  
```
virtual ~agent();
```  
  
### <a name="remarks"></a>备注  
 它是错误销毁不处于终止状态的代理 (或者`agent_done`或`agent_canceled`)。 这可以避免等待代理到达终止状态的析构函数中的类，该类继承`agent`类。  
  
##  <a name="a-namecancela-cancel"></a><a name="cancel"></a>取消 

 将代理移从`agent_created`或`agent_runnable`状态到`agent_canceled`状态。  
  
```
bool cancel();
```  
  
### <a name="return-value"></a>返回值  
 `true`如果代理已被取消，`false`否则为。 如果它已经启动了运行或已完成，代理不能取消。  
  
##  <a name="a-namedonea-done"></a><a name="done"></a>完成 

 将移动到代理`agent_done`状态，指示该代理已完成。  
  
```
bool done();
```  
  
### <a name="return-value"></a>返回值  
 `true`如果代理移动到`agent_done`状态，`false`否则为。 已取消的代理不能移动到`agent_done`状态。  
  
### <a name="remarks"></a>备注  
 此方法应调用的末尾`run`方法，当您知道您的代理执行完成。  
  
##  <a name="a-nameruna-run"></a><a name="run"></a>运行 

 表示代理的主要任务。 `run`应在派生类中重写，并指定代理应执行的操作已启动。  
  
```
virtual void run() = 0;
```  
  
### <a name="remarks"></a>备注  
 代理状态将更改为`agent_started`右键之前调用此方法。 该方法应调用`done`的代理上的相应的状态，然后再返回，并且可能不会引发任何异常。  
  
##  <a name="a-namestarta-start"></a><a name="start"></a>启动 

 将从代理移`agent_created`状态进入`agent_runnable`状态，并且执行对其进行安排。  
  
```
bool start();
```  
  
### <a name="return-value"></a>返回值  
 `true`如果代理是否正确，启动`false`否则为。 无法启动代理程序已被取消。  
  
##  <a name="a-namestatusa-status"></a><a name="status"></a>状态 

 来自代理的状态信息的同步源。  
  
```
agent_status status();
```  
  
### <a name="return-value"></a>返回值  
 返回的代理的当前状态。 请注意在返回后无法更改此返回的状态。  
  
##  <a name="a-namestatusporta-statusport"></a><a name="status_port"></a>status_port 

 来自代理的状态信息异步源。  
  
```
ISource<agent_status>* status_port();
```  
  
### <a name="return-value"></a>返回值  
 返回可以发送有关代理的当前状态的消息的消息源。  
  
##  <a name="a-namewaita-wait"></a><a name="wait"></a>等待 

 等待代理完成其任务。  
  
```
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>参数  
 `_PAgent`  
 指向要等待的代理的指针。  
  
 `_Timeout`  
 若要等待，以毫秒为单位最长时间。  
  
### <a name="return-value"></a>返回值  
 `agent_status`等待完成时的代理。 这可能是`agent_canceled`或`agent_done`。  
  
### <a name="remarks"></a>备注  
 代理任务完成时代理进入`agent_canceled`或`agent_done`状态。  
  
 如果该参数`_Timeout`常数以外的值`COOPERATIVE_TIMEOUT_INFINITE`，异常[operation_timed_out](operation-timed-out-class.md)代理已完成其任务之前，指定的时间内过期时引发。  
  
##  <a name="a-namewaitforalla-waitforall"></a><a name="wait_for_all"></a>wait_for_all 

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
 代理指针数组中存在数目`_PAgents`。  
  
 `_PAgents`  
 指向要等待的代理的指针的数组。  
  
 `_PStatus`  
 指向数组的代理状态的指针。 该方法返回时，每个状态值将表示相应的代理的状态。  
  
 `_Timeout`  
 若要等待，以毫秒为单位最长时间。  
  
### <a name="remarks"></a>备注  
 代理任务完成时代理进入`agent_canceled`或`agent_done`状态。  
  
 如果该参数`_Timeout`常数以外的值`COOPERATIVE_TIMEOUT_INFINITE`，异常[operation_timed_out](operation-timed-out-class.md)代理已完成其任务之前，指定的时间内过期时引发。  
  
##  <a name="a-namewaitforonea-waitforone"></a><a name="wait_for_one"></a>wait_for_one 

 等待指定的代理完成其任务之一。  
  
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
 代理指针数组中存在数目`_PAgents`。  
  
 `_PAgents`  
 指向要等待的代理的指针的数组。  
  
 `_Status`  
 对放置的代理状态的变量的引用。  
  
 `_Index`  
 对将放置代理索引的变量的引用。  
  
 `_Timeout`  
 若要等待，以毫秒为单位最长时间。  
  
### <a name="remarks"></a>备注  
 代理任务完成时代理进入`agent_canceled`或`agent_done`状态。  
  
 如果该参数`_Timeout`常数以外的值`COOPERATIVE_TIMEOUT_INFINITE`，异常[operation_timed_out](operation-timed-out-class.md)代理已完成其任务之前，指定的时间内过期时引发。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

