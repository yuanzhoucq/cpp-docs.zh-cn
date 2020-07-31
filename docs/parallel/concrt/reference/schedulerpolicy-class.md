---
title: SchedulerPolicy 类
ms.date: 11/04/2016
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
ms.openlocfilehash: b7b99dae2ffb58123c05a65872e4c71e149ac12c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219568"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy 类

`SchedulerPolicy` 类包含一组控制计划程序实例的行为的键/值对，一个键/值对对应于一个策略元素。

## <a name="syntax"></a>语法

```cpp
class SchedulerPolicy;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[SchedulerPolicy](#ctor)|已重载。 构造一个新的计划程序策略，并用并发运行时计划程序和资源管理器支持的[策略密钥](concurrency-namespace-enums.md)的值填充它。|
|[~ SchedulerPolicy 析构函数](#dtor)|销毁计划程序策略。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[GetPolicyValue](#getpolicyvalue)|检索作为参数提供的策略密钥的值 `key` 。|
|[SetConcurrencyLimits](#setconcurrencylimits)|同时 `MinConcurrency` `MaxConcurrency` 在对象上设置和策略 `SchedulerPolicy` 。|
|[SetPolicyValue](#setpolicyvalue)|设置作为参数提供的策略密钥的值 `key` ，并返回旧值。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator =](#operator_eq)|从另一个计划程序策略分配计划程序策略。|

## <a name="remarks"></a>备注

有关可使用类控制的策略的详细信息 `SchedulerPolicy` ，请参阅[PolicyElementKey](concurrency-namespace-enums.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SchedulerPolicy`

## <a name="requirements"></a>要求

**标头：** concrt、concrtrm。h

**命名空间：** 并发

## <a name="getpolicyvalue"></a><a name="getpolicyvalue"></a>GetPolicyValue

检索作为参数提供的策略密钥的值 `key` 。

```cpp
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>参数

*key*<br/>
要为其检索值的策略键。

### <a name="return-value"></a>返回值

如果支持参数指定的键 `key` ，则将键强制转换为的策略值 **`unsigned int`** 。

### <a name="remarks"></a>备注

方法将引发无效策略键[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) 。

## <a name="operator"></a><a name="operator_eq"></a>operator =

从另一个计划程序策略分配计划程序策略。

```cpp
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```

### <a name="parameters"></a>参数

*_RhsPolicy*<br/>
要分配给此策略的策略。

### <a name="return-value"></a>返回值

对计划程序策略的引用。

### <a name="remarks"></a>备注

通常，定义新的计划程序策略最方便的方法是复制现有策略并使用 `SetPolicyValue` 或 `SetConcurrencyLimits` 方法对其进行修改。

## <a name="schedulerpolicy"></a><a name="ctor"></a>SchedulerPolicy

构造一个新的计划程序策略，并用并发运行时计划程序和资源管理器支持的[策略密钥](concurrency-namespace-enums.md)的值填充它。

```cpp
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```

### <a name="parameters"></a>参数

*_PolicyKeyCount*<br/>
参数后面的键/值对的数目 `_PolicyKeyCount` 。

*_SrcPolicy*<br/>
要复制的源策略。

### <a name="remarks"></a>备注

第一个构造函数创建新的计划程序策略，所有策略都将初始化为其默认值。

第二个构造函数创建新的计划程序策略，该策略使用命名参数的初始化样式。 参数后的值 `_PolicyKeyCount` 以键/值对的形式提供。 未在此构造函数中指定的任何策略键都将具有其默认值。 此构造函数可能会[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md)、 [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)或[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md)引发异常。

第三个构造函数是复制构造函数。 通常，定义新的计划程序策略最方便的方法是复制现有策略并使用 `SetPolicyValue` 或 `SetConcurrencyLimits` 方法对其进行修改。

## <a name="schedulerpolicy"></a><a name="dtor"></a>~ SchedulerPolicy

销毁计划程序策略。

```cpp
~SchedulerPolicy();
```

## <a name="setconcurrencylimits"></a><a name="setconcurrencylimits"></a>SetConcurrencyLimits

同时 `MinConcurrency` `MaxConcurrency` 在对象上设置和策略 `SchedulerPolicy` 。

```cpp
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>参数

*_MinConcurrency*<br/>
策略密钥的值 `MinConcurrency` 。

*_MaxConcurrency*<br/>
策略密钥的值 `MaxConcurrency` 。

### <a name="remarks"></a>备注

如果为策略指定[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md)的值 `MinConcurrency` 大于为策略指定的值，则该方法将引发 invalid_scheduler_policy_thread_specification `MaxConcurrency` 。

方法还可以为其他无效值引发[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) 。

## <a name="setpolicyvalue"></a><a name="setpolicyvalue"></a>SetPolicyValue

设置作为参数提供的策略密钥的值 `key` ，并返回旧值。

```cpp
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```

### <a name="parameters"></a>参数

*key*<br/>
要为其设置值的策略键。

*value*<br/>
要将策略密钥设置为的值。

### <a name="return-value"></a>返回值

如果支持参数指定的密钥 `key` ，则密钥的旧策略值强制转换为 **`unsigned int`** 。

### <a name="remarks"></a>备注

方法将引发无效策略密钥或其值不能由方法设置的任何策略密钥的[invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) `SetPolicyValue` 。

此方法将引发参数指定的键不支持的值[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) `key` 。

请注意，不允许此方法设置 `MinConcurrency` 或 `MaxConcurrency` 策略。 若要设置这些值，请使用[SetConcurrencyLimits](#setconcurrencylimits)方法。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[CurrentScheduler 类](currentscheduler-class.md)<br/>
[计划程序类](scheduler-class.md)<br/>
[任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
