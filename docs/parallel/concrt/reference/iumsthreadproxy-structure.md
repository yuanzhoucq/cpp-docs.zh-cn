---
title: IUMSThreadProxy 结构
ms.date: 11/04/2016
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
ms.openlocfilehash: 2e748b1da02394e1f70afd8b92947e1291957c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368086"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy 结构

执行线程的抽象。 如果想要计划程序获得用户模式计划 (UMS) 线程，则将计划程序策略元素 `SchedulerKind` 的值设置为 `UmsThreadDefault`，并实现 `IUMSScheduler` 接口。 UMS 线程仅在具有 Windows 7 或更高版本的 64 位操作系统上受到支持。

## <a name="syntax"></a>语法

```cpp
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IUMSThread 代理：：输入关键区域](#entercriticalregion)|调用以进入关键区域。 在关键区域内时，计划程序将不会观察到在该区域期间发生的异步阻塞操作。 这意味着对于 UMS 线程的页面错误、线程挂起、内核异步过程调用 （APC） 等，将不会重新输入计划程序。|
|[IUMSThread 代理：：输入超临界区域](#enterhypercriticalregion)|调用以进入超临界区域。 在超临界区域内时，计划程序将不会观察到该区域期间发生的任何阻塞操作。 这意味着计划程序将不再重新进入 UMS 线程的阻止函数调用、阻止锁定获取尝试、页面错误、线程挂起、内核异步过程调用 (APC) 等。|
|[IUMSThread 代理：：退出关键区域](#exitcriticalregion)|为了退出关键区域而调用。|
|[IUMSThread 代理：：退出超临界区域](#exithypercriticalregion)|调用以退出超关键区域。|
|[IUMSThread 代理：：获取临界区域类型](#getcriticalregiontype)|返回线程代理位于哪类关键区域。 由于超临界区域是关键区域的超集，如果代码已进入关键区域，然后`InsideHyperCriticalRegion`返回一个超临界区域。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>要求

**标题：** concrtrm.h

**命名空间：** 并发

## <a name="iumsthreadproxyentercriticalregion-method"></a><a name="entercriticalregion"></a>IUMSThread 代理：：输入临界区域方法

调用以进入关键区域。 在关键区域内时，计划程序将不会观察到在该区域期间发生的异步阻塞操作。 这意味着对于 UMS 线程的页面错误、线程挂起、内核异步过程调用 （APC） 等，将不会重新输入计划程序。

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>返回值

关键区域的新深度。 关键区域是重入的。

## <a name="iumsthreadproxyenterhypercriticalregion-method"></a><a name="enterhypercriticalregion"></a>IUMSThread 代理：：输入超临界区域方法

调用以进入超临界区域。 在超临界区域内时，计划程序将不会观察到该区域期间发生的任何阻塞操作。 这意味着计划程序将不再重新进入 UMS 线程的阻止函数调用、阻止锁定获取尝试、页面错误、线程挂起、内核异步过程调用 (APC) 等。

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>返回值

超临界区域的新深度。 超临界区域是重入区域。

### <a name="remarks"></a>备注

调度程序必须非常小心调用什么方法，并在此类区域中获取什么锁。 如果此类区域中的代码阻塞了计划程序负责计划的内容所持有的锁上，则可能会出现死锁。

## <a name="iumsthreadproxyexitcriticalregion-method"></a><a name="exitcriticalregion"></a>IUMSThread 代理：：退出关键区域方法

为了退出关键区域而调用。

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>返回值

关键区域的新深度。 关键区域是重入的。

## <a name="iumsthreadproxyexithypercriticalregion-method"></a><a name="exithypercriticalregion"></a>IUMSThread 代理：：退出超临界区域方法

调用以退出超关键区域。

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>返回值

超临界区域的新深度。 超临界区域是重入区域。

## <a name="iumsthreadproxygetcriticalregiontype-method"></a><a name="getcriticalregiontype"></a>IUMSThread 代理：：获取临界区域类型方法

返回线程代理位于哪类关键区域。 由于超临界区域是关键区域的超集，如果代码已进入关键区域，然后`InsideHyperCriticalRegion`返回一个超临界区域。

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>返回值

线程代理位于其中的关键区域的类型。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)<br/>
[IUMSScheduler 结构](iumsscheduler-structure.md)
