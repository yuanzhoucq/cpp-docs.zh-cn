---
title: "IUMSThreadProxy 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 19
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 46d486ddccce6f3c54627f3ea96f001e8e3bfcf7
ms.contentlocale: zh-cn
ms.lasthandoff: 03/17/2017

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
|[Iumsthreadproxy:: Entercriticalregion](#entercriticalregion)|调用以输入临界区。 关键的区域内时计划程序将不会看到异步该区域中发生的阻塞操作。 这意味着计划程序将不再进入页面错误、 线程挂起、 内核异步过程调用 (Apc) 等，UMS 线程的。|  
|[Iumsthreadproxy:: Enterhypercriticalregion](#enterhypercriticalregion)|调用以输入超临界区。 当超关键的区域内，计划程序将不会看到该区域中发生的任何阻止操作。 这意味着计划程序将不再重新进入 UMS 线程的阻止函数调用、阻止锁定获取尝试、页面错误、线程挂起、内核异步过程调用 (APC) 等。|  
|[Iumsthreadproxy:: Exitcriticalregion](#exitcriticalregion)|调用以退出临界区。|  
|[Iumsthreadproxy:: Exithypercriticalregion](#exithypercriticalregion)|调用以退出超临界区。|  
|[Iumsthreadproxy:: Getcriticalregiontype](#getcriticalregiontype)|返回哪种线程代理所处的关键区域。 因为超临界区是临界区的超集，如果代码已进入临界区，然后超临界区，`InsideHyperCriticalRegion`将返回。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [IThreadProxy](ithreadproxy-structure.md)  
  
 `IUMSThreadProxy`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="entercriticalregion"></a>Iumsthreadproxy:: Entercriticalregion 方法  
 调用以输入临界区。 关键的区域内时计划程序将不会看到异步该区域中发生的阻塞操作。 这意味着计划程序将不再进入页面错误、 线程挂起、 内核异步过程调用 (Apc) 等，UMS 线程的。  
  
```
virtual int EnterCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新的临界区深度。 临界区是可重入。  
  
##  <a name="enterhypercriticalregion"></a>Iumsthreadproxy:: Enterhypercriticalregion 方法  
 调用以输入超临界区。 当超关键的区域内，计划程序将不会看到该区域中发生的任何阻止操作。 这意味着计划程序将不再重新进入 UMS 线程的阻止函数调用、阻止锁定获取尝试、页面错误、线程挂起、内核异步过程调用 (APC) 等。  
  
```
virtual int EnterHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新的超临界区深度。 超临界区是可重入。  
  
### <a name="remarks"></a>备注  
 计划程序必须格外注意什么，它调用的方法和其锁定获取在此类区域中。 如果在此类区域中的代码块由计划程序负责计划持有锁，可能会发生死锁。  
  
##  <a name="exitcriticalregion"></a>Iumsthreadproxy:: Exitcriticalregion 方法  
 调用以退出临界区。  
  
```
virtual int ExitCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新的临界区深度。 临界区是可重入。  
  
##  <a name="exithypercriticalregion"></a>Iumsthreadproxy:: Exithypercriticalregion 方法  
 调用以退出超临界区。  
  
```
virtual int ExitHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新的超临界区深度。 超临界区是可重入。  
  
##  <a name="getcriticalregiontype"></a>Iumsthreadproxy:: Getcriticalregiontype 方法  
 返回哪种线程代理所处的关键区域。 因为超临界区是临界区的超集，如果代码已进入临界区，然后超临界区，`InsideHyperCriticalRegion`将返回。  
  
```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 线程代理所处的关键区域的类型。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IUMSScheduler 结构](iumsscheduler-structure.md)

