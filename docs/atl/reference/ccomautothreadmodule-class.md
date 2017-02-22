---
title: "CComAutoThreadModule Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComAutoThreadModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "apartment model modules"
  - "CComAutoThreadModule class"
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CComAutoThreadModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

自ATL 7.0，`CComAutoThreadModule` 已过时:有关详细信息 [ATL模块选件类](../../atl/atl-module-classes.md) 参见。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
class ThreadAllocator= CComSimpleThreadAllocator   
>  
class CComAutoThreadModule :  
public CComModule  
```  
  
#### 参数  
 `ThreadAllocator`  
 \[in\]选件类托管线程选择。  默认值为 [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[CreateInstance](../Topic/CComAutoThreadModule::CreateInstance.md)|处于关联的单元选择线程然后创建对象。|  
|[GetDefaultThreads](../Topic/CComAutoThreadModule::GetDefaultThreads.md)|\(静态\)动态计算的线程数量。具体取决于处理器的数目的模块。|  
|[Init](../Topic/CComAutoThreadModule::Init.md)|创建模块的线程。|  
|[锁定](../Topic/CComAutoThreadModule::Lock.md)|增加锁计数在模块以及当前线程。|  
|[unlock](../Topic/CComAutoThreadModule::Unlock.md)|递减锁计数在模块以及当前线程。|  
  
### 数据成员  
  
### 数据成员  
  
|||  
|-|-|  
|[dwThreadID](../Topic/CComAutoThreadModule::dwThreadID.md)|包含当前线程的标识符。|  
|[m\_Allocator](../Topic/CComAutoThreadModule::m_Allocator.md)|管理线程选择。|  
|[m\_nThreads](../Topic/CComAutoThreadModule::m_nThreads.md)|在模块包含线程的数量。|  
|[m\_pApartments](../Topic/CComAutoThreadModule::m_pApartments.md)|管理模块的单元。|  
  
## 备注  
  
> [!NOTE]
>  此选件类已过时，将 [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) 和 [CAtlModule](../../atl/reference/catlmodule-class.md) 派生类替换。  下面的信息功能上与ATL早期版本的。  
  
 `CComAutoThreadModule` 从 [CComModule](../../atl/reference/ccommodule-class.md) 派生来实现EXE和Windows服务的一线程池的，单元模型COM服务器。  `CComAutoThreadModule` 使用 [CComApartment](../../atl/reference/ccomapartment-class.md) 管理每个线程的一个单元在模块。  
  
 用于在多个单元时，创建对象从 `CComAutoThreadModule` 则应从派生该模块。  您的对象类定义还必须包括 [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) 宏指定 [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) 作为选件类工厂。  
  
 默认情况下，ATL COM AppWizard \(Visual Studio .NET\) ATL项目向导从 `CComModule`将派生自己的模块。  若要使用 `CComAutoThreadModule`，请修改类定义。  例如：  
  
 [!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/CPP/ccomautothreadmodule-class_1.cpp)]  
  
## 继承层次结构  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `IAtlAutoThreadModule`  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 [CComModule](../../atl/reference/ccommodule-class.md)  
  
 `CComAutoThreadModule`  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)