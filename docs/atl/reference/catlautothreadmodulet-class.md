---
title: "CAtlAutoThreadModuleT Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAtlAutoThreadModuleT"
  - "ATL::CAtlAutoThreadModuleT"
  - "CAtlAutoThreadModuleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlAutoThreadModuleT class"
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlAutoThreadModuleT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类为实现线程池提供方法，单元模型COM服务器。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
class T,  
class ThreadAllocator= CComSimpleThreadAllocator,  
DWORD dwWait= INFINITE   
>  
class ATL_NO_VTABLE CAtlAutoThreadModuleT :  
public IAtlAutoThreadModule  
```  
  
#### 参数  
 `T`  
 将实现COM服务器的选件类。  
  
 `ThreadAllocator`  
 选件类托管线程选择。  默认值为 [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。  
  
 `dwWait`  
 以毫秒为单位指定超时间隔。  默认值是无限大的，这意味着方法超时间隔从段。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAtlAutoThreadModuleT::GetDefaultThreads](../Topic/CAtlAutoThreadModuleT::GetDefaultThreads.md)|此静态函数具体取决于处理器的数目动态计算并返回线程的最大数量EXE模块则为;否则为。|  
  
## 备注  
 选件类 [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) 从 `CAtlAutoThreadModuleT` 派生来实现线程池，单元模型COM服务器。  它会替换过期选件类 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。  
  
> [!NOTE]
>  此选件类不应使用DLL，因为默认 `dwWait` 值的无限制将产生一个死锁，当卸载DLL时。  
  
## 继承层次结构  
 `IAtlAutoThreadModule`  
  
 `CAtlAutoThreadModuleT`  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [IAtlAutoThreadModule Class](../../atl/reference/iatlautothreadmodule-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [IAtlAutoThreadModule Class](../../atl/reference/iatlautothreadmodule-class.md)   
 [Module 类](../../atl/atl-module-classes.md)