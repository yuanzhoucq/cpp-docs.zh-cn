---
title: "CAtlBaseModule Class | Microsoft Docs"
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
  - "ATL::CAtlBaseModule"
  - "ATL.CAtlBaseModule"
  - "CAtlBaseModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlBaseModule class"
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlBaseModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类在每个ATL项目实例化。  
  
## 语法  
  
```  
  
   class CAtlBaseModule :  
public _ATL_BASE_MODULE  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAtlBaseModule::CAtlBaseModule](../Topic/CAtlBaseModule::CAtlBaseModule.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAtlBaseModule::AddResourceInstance](../Topic/CAtlBaseModule::AddResourceInstance.md)|将资源添加到实例存储的句柄列表。|  
|[CAtlBaseModule::GetHInstanceAt](../Topic/CAtlBaseModule::GetHInstanceAt.md)|将处理返回到指定的资源例程。|  
|[CAtlBaseModule::GetModuleInstance](../Topic/CAtlBaseModule::GetModuleInstance.md)|返回从 `CAtlBaseModule` 对象的模块实例。|  
|[CAtlBaseModule::GetResourceInstance](../Topic/CAtlBaseModule::GetResourceInstance.md)|返回从 `CAtlBaseModule` 对象的资源实例。|  
|[CAtlBaseModule::RemoveResourceInstance](../Topic/CAtlBaseModule::RemoveResourceInstance.md)|从存储的处理列表中移除资源例程。|  
|[CAtlBaseModule::SetResourceInstance](../Topic/CAtlBaseModule::SetResourceInstance.md)|设置 `CAtlBaseModule` 对象的资源实例。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAtlBaseModule::m\_bInitFailed](../Topic/CAtlBaseModule::m_bInitFailed.md)|指示的变量初始化模块是否已失败。|  
  
## 备注  
 `CAtlBaseModule` 实例命名为\_AtlBaseModule存在于每个ATL项目，包含处理对于模块实例，请处理到包含模块默认情况下，将为相同的\)的资源\(和一组句柄提供主资源的模块。  `CAtlBaseModule` 可以从多个线程安全访问。  
  
 此选件类替换为使用ATL的早期版本的过时 [CComModule](../../atl/reference/ccommodule-class.md) 选件类。  
  
## 继承层次结构  
 [\_ATL\_BASE\_MODULE](../Topic/_ATL_BASE_MODULE.md)  
  
 `CAtlBaseModule`  
  
## 要求  
 **Header:** atlcore.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)