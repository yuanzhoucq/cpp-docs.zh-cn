---
title: "Threading Models and Critical Sections Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.threads.models"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, critical sections"
  - "ATL, 多线程处理"
  - "critical sections"
  - "线程处理 [ATL], 模型"
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Threading Models and Critical Sections Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面选件类定义了线程模型和临界区:  
  
-   [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md) 实现线程池，单元模型COM服务器。  
  
-   [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md) 为实现线程池提供方法，单元模型COM服务器。  
  
-   [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md) 为递增和递减变量提供线程安全的方法。  提供临界区。  
  
-   [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md) 为递增和递减变量提供线程安全的方法。  不提供临界区。  
  
-   [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md) 为递增和递减变量的方法。  不提供临界区。  
  
-   [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) 确定单个对象类的适当线程模型选件类。  
  
-   [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md) 确定是全局可用的对象的适当线程模型选件类。  
  
-   [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md) 包含获取和释放临界区的方法。  临界区自动初始化。  
  
-   [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md) 包含获取和释放临界区的方法。  必须显式初始化临界区。  
  
-   [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md) 反射在 `CComCriticalSection` 的方法，而不提供临界区。  在 `CComFakeCriticalSection` 的方法不执行任何操作。  
  
-   [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) 为CRT线程提供创建功能。  如果线程将使用CRT函数，请使用此选件类。  
  
-   [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md) 对于Windows线程提供创建功能。  如果线程不使用CRT函数，请使用此选件类。  
  
## 请参阅  
 [Class Overview](../atl/atl-class-overview.md)