---
title: 线程处理模型和临界区类 (ATL) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- vc.atl.threads.models
dev_langs:
- C++
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37172c0080664f496bdf5d5c7c0ebecbd8f77898
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="threading-models-and-critical-sections-classes"></a>线程处理模型和临界区类
下面的类定义线程处理模型和临界区：  
  
-   [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md)实现线程放入池中，单元模型的 COM 服务器。  
  
-   [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md)提供用于实现线程放入池中，单元模型 COM 服务器的方法。  
  
-   [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md)递增和递减的变量提供线程安全的方法。 提供一个临界区。  
  
-   [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md)递增和递减的变量提供线程安全的方法。 不提供关键部分。  
  
-   [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md)提供用于递增和递减值变量的方法。 不提供关键部分。  
  
-   [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel)确定单个对象类的适当线程处理模型类。  
  
-   [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel)确定一个对象，它全局可用的适当线程处理模型类。  
  
-   [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md)包含用于获取和释放临界区的方法。 临界区将自动进行初始化。  
  
-   [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md)包含用于获取和释放临界区的方法。 必须显式初始化的关键部分。  
  
-   [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md)镜像中的方法`CComCriticalSection`而无需提供一个临界区。 中的方法`CComFakeCriticalSection`不执行任何操作。  
  
-   [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) CRT 线程提供创建函数。 如果线程将使用的 CRT 函数，请使用此类。  
  
-   [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md)提供 Windows 线程创建函数。 如果线程将不会使用 CRT 函数，请使用此类。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../atl/atl-class-overview.md)

