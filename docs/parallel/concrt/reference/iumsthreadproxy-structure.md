---
title: "IUMSThreadProxy 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::IUMSThreadProxy
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
translationtype: Machine Translation
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: 55ed05f137775e819c81ce231cf8c8ad3a9974f3
ms.lasthandoff: 02/24/2017

---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy 结构
执行线程的抽象。 如果想要计划程序获得用户模式计划 (UMS) 线程，则将计划程序策略元素 `SchedulerKind` 的值设置为 `UmsThreadDefault`，并实现 `IUMSScheduler` 接口。 UMS 线程仅在具有 Windows 7 或更高版本的 64 位操作系统上受到支持。  
  
## <a name="syntax"></a>语法  
  
```
struct IUMSThreadProxy : public IThreadProxy;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[Iumsthreadproxy:: Entercriticalregion 方法](#entercriticalregion)|调用以输入临界区。 关键的区域内时计划程序将不会看到异步该区域中发生的阻塞操作。 这意味着计划程序将不再进入页面错误、 线程挂起、 内核异步过程调用 (Apc) 等，UMS 线程的。|  
|[Iumsthreadproxy:: Enterhypercriticalregion 方法](#enterhypercriticalregion)|调用以输入超临界区。 当超关键的区域内，计划程序将不会看到该区域中发生的任何阻止操作。 这意味着计划程序将不再重新进入 UMS 线程的阻止函数调用、阻止锁定获取尝试、页面错误、线程挂起、内核异步过程调用 (APC) 等。|  
|[Iumsthreadproxy:: Exitcriticalregion 方法](#exitcriticalregion)|调用以退出临界区。|  
|[Iumsthreadproxy:: Exithypercriticalregion 方法](#exithypercriticalregion)|调用以退出超临界区。|  
|[Iumsthreadproxy:: Getcriticalregiontype 方法](#getcriticalregiontype)|返回哪种线程代理所处的关键区域。 因为超临界区是临界区的超集，如果代码已进入临界区，然后超临界区，`InsideHyperCriticalRegion`将返回。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [IThreadProxy](ithreadproxy-structure.md)  
  
 `IUMSThreadProxy`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="a-nameentercriticalregiona--iumsthreadproxyentercriticalregion-method"></a><a name="entercriticalregion"></a>Iumsthreadproxy:: Entercriticalregion 方法  
 调用以输入临界区。 关键的区域内时计划程序将不会看到异步该区域中发生的阻塞操作。 这意味着计划程序将不再进入页面错误、 线程挂起、 内核异步过程调用 (Apc) 等，UMS 线程的。  
  
```
virtual int EnterCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新的临界区深度。 临界区是可重入。  
  
##  <a name="a-nameenterhypercriticalregiona--iumsthreadproxyenterhypercriticalregion-method"></a><a name="enterhypercriticalregion"></a>Iumsthreadproxy:: Enterhypercriticalregion 方法  
 调用以输入超临界区。 当超关键的区域内，计划程序将不会看到该区域中发生的任何阻止操作。 这意味着计划程序将不再重新进入 UMS 线程的阻止函数调用、阻止锁定获取尝试、页面错误、线程挂起、内核异步过程调用 (APC) 等。  
  
```
virtual int EnterHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新的超临界区深度。 超临界区是可重入。  
  
### <a name="remarks"></a>备注  
 计划程序必须格外注意什么，它调用的方法和其锁定获取在此类区域中。 如果在此类区域中的代码块由计划程序负责计划持有锁，可能会发生死锁。  
  
##  <a name="a-nameexitcriticalregiona--iumsthreadproxyexitcriticalregion-method"></a><a name="exitcriticalregion"></a>Iumsthreadproxy:: Exitcriticalregion 方法  
 调用以退出临界区。  
  
```
virtual int ExitCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新的临界区深度。 临界区是可重入。  
  
##  <a name="a-nameexithypercriticalregiona--iumsthreadproxyexithypercriticalregion-method"></a><a name="exithypercriticalregion"></a>Iumsthreadproxy:: Exithypercriticalregion 方法  
 调用以退出超临界区。  
  
```
virtual int ExitHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新的超临界区深度。 超临界区是可重入。  
  
##  <a name="a-namegetcriticalregiontypea--iumsthreadproxygetcriticalregiontype-method"></a><a name="getcriticalregiontype"></a>Iumsthreadproxy:: Getcriticalregiontype 方法  
 返回哪种线程代理所处的关键区域。 因为超临界区是临界区的超集，如果代码已进入临界区，然后超临界区，`InsideHyperCriticalRegion`将返回。  
  
```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 线程代理所处的关键区域的类型。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IUMSScheduler 结构](iumsscheduler-structure.md)

