---
title: "ScheduleGroup 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
dev_langs:
- C++
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
caps.latest.revision: 20
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: dc7a78fd135d56e1243c43672172e433652e34e2
ms.lasthandoff: 03/17/2017

---
# <a name="schedulegroup-class"></a>ScheduleGroup 类
表示计划组的抽象。 计划组整理受益于在时间上（通过在移动到另一个组之前执行同一个组中的另一个任务）或空间上（通过在同一 NUMA 节点或物理套接字上执行同一个组内的多个项）紧密计划在一起的一组相关工作。  
  
## <a name="syntax"></a>语法  
  
```
class ScheduleGroup;
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[~ ScheduleGroup 析构函数](#dtor)||  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Id](#id)|返回组所属的计划程序中是唯一的计划组的标识符。|  
|[参考](#reference)|递增计划组的引用计数。|  
|[发布](#release)|递减计划程序组的引用计数。|  
|[ScheduleTask](#scheduletask)|计划的计划组中的轻量任务。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ScheduleGroup`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="id"></a>Id 

 返回组所属的计划程序中是唯一的计划组的标识符。  
  
```
virtual unsigned int Id() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 在组所属的计划程序中是唯一的计划组标识符。  
  
##  <a name="operator_delete"></a>运算符 delete 

 一个`ScheduleGroup`对象被销毁内部运行时在发布给它的所有外部引用。 不能显式删除它。  
  
```
void operator delete(
    void* _PObject);

void operator delete(
    void* _PObject,
    int,
 const char *,
    int);
```    
  
### <a name="parameters"></a>参数  
 `_PObject`  
 指向要删除的对象的指针。  
  
##  <a name="reference"></a>引用 

 递增计划组的引用计数。  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新增加的引用计数。  
  
### <a name="remarks"></a>备注  
 这通常用于管理复合计划组的生存期。 当计划组的引用计数降到零时，计划组将删除由运行时。 创建使用计划组[currentscheduler:: Createschedulegroup](currentscheduler-class.md#createschedulegroup)方法，或[scheduler:: createschedulegroup](scheduler-class.md#createschedulegroup)方法首先之一的引用计数。  
  
##  <a name="release"></a>版本 

 递减计划程序组的引用计数。  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新递减引用计数。  
  
### <a name="remarks"></a>备注  
 这通常用于管理复合计划组的生存期。 当计划组的引用计数降到零时，计划组将删除由运行时。 调用 `Release` 方法特定次数来移除创建引用数和使用 `Reference` 方法放置的任何其他引用后，您将无法进一步使用计划组。 这样做将导致未定义的行为。  
  
 计划组都与特定计划程序实例相关联。 必须确保对于计划组的所有引用都在所有对计划程序的引用释放之前释放，因为后者可能导致计划程序破坏。 这样做; 否则为会导致未定义的行为。  
  
##  <a name="dtor"></a>~ ScheduleGroup 

```
virtual ~ScheduleGroup();
```  
  
##  <a name="scheduletask"></a>ScheduleTask 

 计划的计划组中的轻量任务。  
  
```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_Proc`  
 指向要执行来执行轻量任务的主体的函数的指针。  
  
 `_Data`  
 指向将作为参数传递给任务的主体的数据的 void 指针。  
  
### <a name="remarks"></a>备注  
 调用`ScheduleTask`方法隐式将引用计数放在适当的时间后执行该任务时由运行时删除的计划组上。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [CurrentScheduler 类](currentscheduler-class.md)   
 [Scheduler 类](scheduler-class.md)   
 [任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)




