---
title: "CAtlModuleT Class | Microsoft Docs"
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
  - "ATL::CAtlModuleT<T>"
  - "ATL.CAtlModuleT"
  - "ATL.CAtlModuleT<T>"
  - "ATL::CAtlModuleT"
  - "CAtlModuleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlModuleT class"
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlModuleT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现一个ATL模块。  
  
## 语法  
  
```  
  
      template <  
   class T   
>   
class ATL_NO_VTABLE CAtlModuleT :  
   public CAtlModule  
```  
  
#### 参数  
 `T`  
 从 `CAtlModuleT`派生的选件类。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAtlModuleT::CAtlModuleT](../Topic/CAtlModuleT::CAtlModuleT.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAtlModuleT::InitLibId](../Topic/CAtlModuleT::InitLibId.md)|初始化包含当前模块的GUID的数据成员。|  
|[CAtlModuleT::RegisterAppId](../Topic/CAtlModuleT::RegisterAppId.md)|添加EXE到注册表。|  
|[CAtlModuleT::RegisterServer](../Topic/CAtlModuleT::RegisterServer.md)|添加服务添加到注册表。|  
|[CAtlModuleT::UnregisterAppId](../Topic/CAtlModuleT::UnregisterAppId.md)|从注册表中移除EXE。|  
|[CAtlModuleT::UnregisterServer](../Topic/CAtlModuleT::UnregisterServer.md)|从注册表中移除服务。|  
|[CAtlModuleT::UpdateRegistryAppId](../Topic/CAtlModuleT::UpdateRegistryAppId.md)|更新在注册表的EXE信息。|  
  
## 备注  
 `CAtlModuleT`，从派生 [CAtlModule](../../atl/reference/catlmodule-class.md)，实现一个可执行\(exe\)或一个服务\(exe\) ATL模块。  一个可执行模块是局部的，进程外服务器，而命令舵是在后台运行的Windows应用程序，当Windows启动时。  
  
 `CAtlModuleT` 提供用于初始化，注册和注销模块支持。  
  
## 继承层次结构  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `CAtlModuleT`  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [CAtlModule Class](../../atl/reference/catlmodule-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)