---
title: "IUMSThreadProxy 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
dev_langs:
- C++
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 484c5a8fe7f730bf772fb65dee087ccbe1ff6425
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy 结构
执行线程的抽象。 如果想要计划程序获得用户模式计划 (UMS) 线程，则将计划程序策略元素 `SchedulerKind` 的值设置为 `UmsThreadDefault`，并实现 `IUMSScheduler` 接口。 UMS 线程仅在具有 Windows 7 或更高版本的 64 位操作系统上受到支持。  
  
## <a name="syntax"></a>语法  
  
```
struct IUMSThreadProxy : public IThreadProxy;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IUMSThreadProxy::EnterCriticalRegion](#entercriticalregion)|调用以输入关键区域。 关键的区域内时计划程序将不遵循该区域中发生的异步阻止操作。 这意味着计划程序将不进入页错误、 线程挂起、 内核异步过程调用 (Apc) 等，UMS 线程的。|  
|[IUMSThreadProxy::EnterHyperCriticalRegion](#enterhypercriticalregion)|调用以输入超关键区域。 超关键的区域内时计划程序将不会看到该区域中发生的任何阻止操作。 这意味着计划程序将不再重新进入 UMS 线程的阻止函数调用、阻止锁定获取尝试、页面错误、线程挂起、内核异步过程调用 (APC) 等。|  
|[IUMSThreadProxy::ExitCriticalRegion](#exitcriticalregion)|调用以退出关键区域。|  
|[IUMSThreadProxy::ExitHyperCriticalRegion](#exithypercriticalregion)|调用以退出超关键区域。|  
|[IUMSThreadProxy::GetCriticalRegionType](#getcriticalregiontype)|返回哪种类型的线程代理所处的关键区域。 因为超关键区域是关键区域的一个超集，如果代码已进入关键区域，然后选择超关键的区域，`InsideHyperCriticalRegion`将返回。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [IThreadProxy](ithreadproxy-structure.md)  
  
 `IUMSThreadProxy`  
  
## <a name="requirements"></a>惠?  
 **标头：** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="entercriticalregion"></a>  Iumsthreadproxy:: Entercriticalregion 方法  
 调用以输入关键区域。 关键的区域内时计划程序将不遵循该区域中发生的异步阻止操作。 这意味着计划程序将不进入页错误、 线程挂起、 内核异步过程调用 (Apc) 等，UMS 线程的。  
  
```
virtual int EnterCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新关键区域的深度。 关键区域是可重入。  
  
##  <a name="enterhypercriticalregion"></a>  Iumsthreadproxy:: Enterhypercriticalregion 方法  
 调用以输入超关键区域。 超关键的区域内时计划程序将不会看到该区域中发生的任何阻止操作。 这意味着计划程序将不再重新进入 UMS 线程的阻止函数调用、阻止锁定获取尝试、页面错误、线程挂起、内核异步过程调用 (APC) 等。  
  
```
virtual int EnterHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新超关键区域的深度。 超关键区域是可重入。  
  
### <a name="remarks"></a>备注  
 计划程序必须格外小心有关新增功能，它调用的方法和其锁定获取在此类区域中。 如果此类区域中的代码块由调度器负责计划持有的锁，可能会发生死锁。  
  
##  <a name="exitcriticalregion"></a>  Iumsthreadproxy:: Exitcriticalregion 方法  
 调用以退出关键区域。  
  
```
virtual int ExitCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新关键区域的深度。 关键区域是可重入。  
  
##  <a name="exithypercriticalregion"></a>  Iumsthreadproxy:: Exithypercriticalregion 方法  
 调用以退出超关键区域。  
  
```
virtual int ExitHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新超关键区域的深度。 超关键区域是可重入。  
  
##  <a name="getcriticalregiontype"></a>  IUMSThreadProxy::GetCriticalRegionType Method  
 返回哪种类型的线程代理所处的关键区域。 因为超关键区域是关键区域的一个超集，如果代码已进入关键区域，然后选择超关键的区域，`InsideHyperCriticalRegion`将返回。  
  
```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 线程代理所处的关键区域的类型。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IUMSScheduler 结构](iumsscheduler-structure.md)
