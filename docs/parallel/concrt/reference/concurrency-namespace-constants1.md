---
title: 并发命名空间常量
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::AgentEventGuid
- concrt/concurrency::COOPERATIVE_TIMEOUT_INFINITE
- concrt/concurrency::COOPERATIVE_WAIT_TIMEOUT
- concrt/concurrency::ConcRTEventGuid
- concrt/concurrency::ConcRT_ProviderGuid
- concrt/concurrency::INHERIT_THREAD_PRIORITY
- concrt/concurrency::LockEventGuid
- concrt/concurrency::PPLParallelForEventGuid
- concrt/concurrency::PPLParallelForeachEventGuid
- concrt/concurrency::ResourceManagerEventGuid
- concrt/concurrency::ScheduleGroupEventGuid
- concrt/concurrency::VirtualProcessorEventGuid
ms.assetid: 6f81fc4c-b10c-479e-8717-9c292360d5a0
ms.openlocfilehash: 8e9254e966f480538d80721bcfd86d301fac8d09
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372733"
---
# <a name="concurrency-namespace-constants"></a>并发命名空间常量

||||
|-|-|-|
|[代理事件](#agenteventguid)|[CONCRT_RM_VERSION_1](#concrt_rm_version_1)|[COOPERATIVE_TIMEOUT_INFINITE](#cooperative_timeout_infinite)|
|[COOPERATIVE_WAIT_TIMEOUT](#cooperative_wait_timeout)|[乔雷埃文吉德](#choreeventguid)|[康克RT事件吉德](#concrteventguid)|
|[ConcRT_ProviderGuid](#concrt_providerguid)|[上下文事件吉德](#contexteventguid)|[INHERIT_THREAD_PRIORITY](#inherit_thread_priority)|
|[洛克·埃金吉](#lockeventguid)|[最大执行资源](#maxexecutionresources)|[PPLParallelforEventGuid](#pplparallelforeventguid)|
|[PPLParallelforeach 事件](#pplparallelforeacheventguid)|[PPLParallelInvokeEventGuid](#pplparallelinvokeeventguid)|[资源经理](#resourcemanagereventguid)|
|[计划组事件](#schedulegroupeventguid)|[计划活动](#schedulereventguid)|[虚拟处理器事件](#virtualprocessoreventguid)|

## <a name="agenteventguid"></a><a name="agenteventguid"></a>代理事件

类别 GUID ({B9B5B78C-0713-4898-A21A-C67949DCED07})，描述并发运行时中由代理库激发的 ETW 事件。

```cpp
const __declspec(selectany) GUID AgentEventGuid = {0xb9b5b78c, 0x713, 0x4898, { 0xa2, 0x1a, 0xc6, 0x79, 0x49, 0xdc, 0xed, 0x7 } };
```

## <a name="choreeventguid"></a><a name="choreeventguid"></a>乔雷埃文吉德

类别 GUID，描述由与日常任务或任务直接相关的并发运行时激发的 ETW 事件。

```cpp
const __declspec(selectany) GUID ChoreEventGuid =
    { 0x7E854EC7, 0xCDC4, 0x405a, { 0xB5, 0xB2, 0xAA, 0xF7, 0xC9, 0xE7, 0xD4, 0x0C } };
```

### <a name="remarks"></a>备注

此类别的事件当前不由并发运行时触发。

## <a name="concrt_providerguid"></a><a name="concrt_providerguid"></a>ConcRT_ProviderGuid

并发运行时的 ETW 提供程序 GUID。

```cpp
const __declspec(selectany) GUID ConcRT_ProviderGuid =
    { 0xF7B697A3, 0x4DB5, 0x4d3b, { 0xBE, 0x71, 0xC4, 0xD2, 0x84, 0xE6, 0x59, 0x2F } };
```

## <a name="concrt_rm_version_1"></a><a name="concrt_rm_version_1"></a>CONCRT_RM_VERSION_1

指示支持 Visual Studio 2010 中定义的资源管理器接口。

```cpp
const unsigned int CONCRT_RM_VERSION_1 = 0x00010000;
```

## <a name="concrteventguid"></a><a name="concrteventguid"></a>康克RT事件吉德

类别 GUID，描述由并发运行时激发的且没有被另一个类别进行更具体描述的 ETW 事件。

```cpp
const __declspec(selectany) GUID ConcRTEventGuid =
    { 0x72B14A7D, 0x704C, 0x423e, { 0x92, 0xF8, 0x7E, 0x6D, 0x64, 0xBC, 0xB9, 0x2A } };
```

### <a name="remarks"></a>备注

此类别的事件当前不由并发运行时触发。

## <a name="cooperative_timeout_infinite"></a><a name="cooperative_timeout_infinite"></a>COOPERATIVE_TIMEOUT_INFINITE

指示等待永远不应超时的值。

```cpp
const unsigned int COOPERATIVE_TIMEOUT_INFINITE = (unsigned int)-1;
```

## <a name="cooperative_wait_timeout"></a><a name="cooperative_wait_timeout"></a>COOPERATIVE_WAIT_TIMEOUT

指示等待超时的值。

```cpp
const size_t COOPERATIVE_WAIT_TIMEOUT = SIZE_MAX;
```

## <a name="contexteventguid"></a><a name="contexteventguid"></a>上下文事件吉德

类别 GUID，描述由与上下文直接相关的并发运行时激发的 ETW 事件。

```cpp
const __declspec(selectany) GUID ContextEventGuid =
    { 0x5727A00F, 0x50BE, 0x4519, { 0x82, 0x56, 0xF7, 0x69, 0x98, 0x71, 0xFE, 0xCB } };
```

## <a name="inherit_thread_priority"></a><a name="inherit_thread_priority"></a>INHERIT_THREAD_PRIORITY

策略键 `ContextPriority` 的特殊值，指示计划程序中所有上下文的线程优先级都应与创建该计划程序的线程的优先级相同。

```cpp
const unsigned int INHERIT_THREAD_PRIORITY = 0x0000F000;
```

## <a name="lockeventguid"></a><a name="lockeventguid"></a>洛克·埃金吉

类别 GUID，描述由与锁直接相关的并发运行时激发的 ETW 事件。

```cpp
const __declspec(selectany) GUID LockEventGuid =
    { 0x79A60DC6, 0x5FC8, 0x4952, { 0xA4, 0x1C, 0x11, 0x63, 0xAE, 0xEC, 0x5E, 0xB8 } };
```

### <a name="remarks"></a>备注

此类别的事件当前不由并发运行时触发。

## <a name="maxexecutionresources"></a><a name="maxexecutionresources"></a>最大执行资源

策略键 `MinConcurrency` 和 `MaxConcurrency` 的特殊值。 默认值为没有其他约束的计算机上的硬件线程数。

```cpp
const unsigned int MaxExecutionResources = 0xFFFFFFFF;
```

## <a name="pplparallelforeventguid"></a><a name="pplparallelforeventguid"></a>PPLParallelforEventGuid

类别 GUID，描述由与 `parallel_for` 函数的用法直接相关的并发运行时激发的 ETW 事件。

```cpp
const __declspec(selectany) GUID PPLParallelForEventGuid =
    { 0x31c8da6b, 0x6165, 0x4042, { 0x8b, 0x92, 0x94, 0x9e, 0x31, 0x5f, 0x4d, 0x84 } };
```

## <a name="pplparallelforeacheventguid"></a><a name="pplparallelforeacheventguid"></a>PPLParallelforeach 事件

类别 GUID，描述由与 `parallel_for_each` 函数的用法直接相关的并发运行时激发的 ETW 事件。

```cpp
const __declspec(selectany) GUID PPLParallelForeachEventGuid =
    { 0x5cb7d785, 0x9d66, 0x465d, { 0xba, 0xe1, 0x46, 0x11, 0x6, 0x1b, 0x54, 0x34 } };
```

## <a name="pplparallelinvokeeventguid"></a><a name="pplparallelinvokeeventguid"></a>PPLParallelInvokeEventGuid

类别 GUID，描述由与 `parallel_invoke` 函数的用法直接相关的并发运行时激发的 ETW 事件。

```cpp
const __declspec(selectany) GUID PPLParallelInvokeEventGuid =
    { 0xd1b5b133, 0xec3d, 0x49f4, { 0x98, 0xa3, 0x46, 0x4d, 0x1a, 0x9e, 0x46, 0x82 } };
```

## <a name="resourcemanagereventguid"></a><a name="resourcemanagereventguid"></a>资源经理

类别 GUID，描述由与资源管理器直接相关的并发运行时激发的 ETW 事件。

```cpp
const __declspec(selectany) GUID ResourceManagerEventGuid =
    { 0x2718D25B, 0x5BF5, 0x4479, { 0x8E, 0x88, 0xBA, 0xBC, 0x64, 0xBD, 0xBF, 0xCA } };
```

### <a name="remarks"></a>备注

此类别的事件当前不由并发运行时触发。

## <a name="schedulegroupeventguid"></a><a name="schedulegroupeventguid"></a>计划组事件

类别 GUID，描述由与计划组直接相关的并发运行时激发的 ETW 事件。

```cpp
const __declspec(selectany) GUID ScheduleGroupEventGuid =
    { 0xE8A3BF1F, 0xA86B, 0x4390, { 0x9C, 0x60, 0x53, 0x90, 0xB9, 0x69, 0xD2, 0x2C } };
```

### <a name="remarks"></a>备注

此类别的事件当前不由并发运行时触发。

## <a name="schedulereventguid"></a><a name="schedulereventguid"></a>计划活动

类别 GUID，描述由与计划程序活动直接相关的并发运行时激发的 ETW 事件。

```cpp
const __declspec(selectany) GUID SchedulerEventGuid =
    { 0xE2091F8A, 0x1E0A, 0x4731, { 0x84, 0xA2, 0x0D, 0xD5, 0x7C, 0x8A, 0x52, 0x61 } };
```

## <a name="virtualprocessoreventguid"></a><a name="virtualprocessoreventguid"></a>虚拟处理器事件

类别 GUID，描述由与虚拟处理器直接相关的并发运行时激发的 ETW 事件。

```cpp
const __declspec(selectany) GUID VirtualProcessorEventGuid =
    { 0x2f27805f, 0x1676, 0x4ecc, { 0x96, 0xfa, 0x7e, 0xb0, 0x9d, 0x44, 0x30, 0x2f } };
```

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)
