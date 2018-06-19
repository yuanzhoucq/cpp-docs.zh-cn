---
title: SchedulerPolicy 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
dev_langs:
- C++
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f23e95bafa9920c520fa7c01518873769945770
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691776"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy 类
`SchedulerPolicy` 类包含一组控制计划程序实例的行为的键/值对，一个键/值对对应于一个策略元素。  
  
## <a name="syntax"></a>语法  
  
```
class SchedulerPolicy;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[SchedulerPolicy](#ctor)|已重载。 构造一个新的计划程序策略并使用值填充该[策略键](concurrency-namespace-enums.md)并发运行时计划程序和资源管理器支持。|  
|[~ SchedulerPolicy 析构函数](#dtor)|销毁计划程序策略。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[GetPolicyValue](#getpolicyvalue)|检索的策略键的值作为提供`key`参数。|  
|[SetConcurrencyLimits](#setconcurrencylimits)|同时设置`MinConcurrency`和`MaxConcurrency`上的策略`SchedulerPolicy`对象。|  
|[SetPolicyValue](#setpolicyvalue)|设置的策略键的值作为提供`key`参数并返回旧值。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator=](#operator_eq)|从另一个计划程序策略分配计划程序策略。|  
  
## <a name="remarks"></a>备注  
 有关策略的使用进行控制的详细信息`SchedulerPolicy`类，请参阅[PolicyElementKey](concurrency-namespace-enums.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `SchedulerPolicy`  
  
## <a name="requirements"></a>要求  
 **标头：** concrt.h、 concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="getpolicyvalue"></a> GetPolicyValue 

 检索的策略键的值作为提供`key`参数。  
  
```
unsigned int GetPolicyValue(PolicyElementKey key) const;
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要检索的值的策略键。  
  
### <a name="return-value"></a>返回值  
 如果指定的键`key`支持参数，该密钥的策略值强制转换为`unsigned int`。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md)为无效的策略键。  
  
##  <a name="operator_eq"></a> 运算符 = 

 从另一个计划程序策略分配计划程序策略。  
  
```
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```  
  
### <a name="parameters"></a>参数  
 `_RhsPolicy`  
 要将分配给此策略的策略。  
  
### <a name="return-value"></a>返回值  
 对计划程序策略的引用。  
  
### <a name="remarks"></a>备注  
 通常，定义新的计划程序策略最方便的方法是复制现有策略并使用 `SetPolicyValue` 或 `SetConcurrencyLimits` 方法对其进行修改。  
  
##  <a name="ctor"></a> SchedulerPolicy 

 构造一个新的计划程序策略并使用值填充该[策略键](concurrency-namespace-enums.md)并发运行时计划程序和资源管理器支持。  
  
```
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
 ...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```  
  
### <a name="parameters"></a>参数  
 `_PolicyKeyCount`  
 键/值数对后面`_PolicyKeyCount`参数。  
  
 `_SrcPolicy`  
 要复制的源策略。  
  
### <a name="remarks"></a>备注  
 第一个构造函数创建一个新的计划程序策略，其中的所有策略将都初始化为其默认值。  
  
 第二个构造函数创建一个新的计划程序策略，使用名为参数的初始化的样式。 之后的值`_PolicyKeyCount`以键/值对的形式提供参数。 此构造函数中未指定任何策略项都具有其默认值。 此构造函数可能会引发异常[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md)， [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)或[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).  
  
 第三个构造函数是复制构造函数。 通常，定义新的计划程序策略最方便的方法是复制现有策略并使用 `SetPolicyValue` 或 `SetConcurrencyLimits` 方法对其进行修改。  
  
##  <a name="dtor"></a> ~ SchedulerPolicy 

 销毁计划程序策略。  
  
```
~SchedulerPolicy();
```  
  
##  <a name="setconcurrencylimits"></a> SetConcurrencyLimits 

 同时设置`MinConcurrency`和`MaxConcurrency`上的策略`SchedulerPolicy`对象。  
  
```
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```  
  
### <a name="parameters"></a>参数  
 `_MinConcurrency`  
 值`MinConcurrency`策略密钥。  
  
 `_MaxConcurrency`  
 值`MaxConcurrency`策略密钥。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md)如果指定的值`MinConcurrency`策略大于为指定`MaxConcurrency`策略。  
  
 该方法还会引发[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)有关其他无效值。  
  
##  <a name="setpolicyvalue"></a> SetPolicyValue 

 设置的策略键的值作为提供`key`参数并返回旧值。  
  
```
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要设置的值的策略键。  
  
 `value`  
 要将策略键设置为的值。  
  
### <a name="return-value"></a>返回值  
 如果指定的键`key`支持参数、 键的旧策略值强制转换为`unsigned int`。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md)无效的策略键或其值不能通过设置任何策略密钥`SetPolicyValue`方法。  
  
 该方法将引发[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)不支持指定的键的值`key`参数。  
  
 请注意，此方法不允许设置`MinConcurrency`或`MaxConcurrency`策略。 若要设置这些值，使用[SetConcurrencyLimits](#setconcurrencylimits)方法。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [CurrentScheduler 类](currentscheduler-class.md)   
 [Scheduler 类](scheduler-class.md)   
 [任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



