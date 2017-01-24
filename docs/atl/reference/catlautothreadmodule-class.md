---
title: "CAtlAutoThreadModule Class | Microsoft Docs"
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
  - "ATL.CAtlAutoThreadModule"
  - "CAtlAutoThreadModule"
  - "ATL::CAtlAutoThreadModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlAutoThreadModule class"
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlAutoThreadModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现一线程池，单元模型COM服务器。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      class CAtlAutoThreadModule :  
public CAtlAutoThreadModuleT< CAtlAutoThreadModule >  
```  
  
## 备注  
 `CAtlAutoThreadModule` 从 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) 派生并实现线程池，单元模型COM服务器。  `CAtlAutoThreadModule` 使用 [CComApartment](../../atl/reference/ccomapartment-class.md) 管理每个线程的一个单元在模块。  
  
 您在对象类定义必须使用 [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) 宏指定 [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) 作为选件类工厂。  然后应添加从 `CAtlAutoThreadModuleT` 派生的选件类的一个实例例如 `CAtlAutoThreadModule`。  例如：  
  
 `CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`  
  
> [!NOTE]
>  此选件类替换为过时 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) 选件类。  
  
## 继承层次结构  
 `IAtlAutoThreadModule`  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 `CAtlAutoThreadModule`  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [CAtlAutoThreadModuleT Class](../../atl/reference/catlautothreadmodulet-class.md)   
 [IAtlAutoThreadModule Class](../../atl/reference/iatlautothreadmodule-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)