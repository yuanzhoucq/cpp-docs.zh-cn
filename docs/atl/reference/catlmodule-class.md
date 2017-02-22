---
title: "CAtlModule Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAtlModule"
  - "CAtlModule"
  - "ATL.CAtlModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlModule class"
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CAtlModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供了若干ATL模块选件类的方法。  
  
## 语法  
  
```  
  
   class ATL_NO_VTABLE CAtlModule :  
public _ATL_MODULE  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAtlModule::CAtlModule](../Topic/CAtlModule::CAtlModule.md)|构造函数。|  
|[CAtlModule::~CAtlModule](../Topic/CAtlModule::~CAtlModule.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAtlModule::AddCommonRGSReplacements](../Topic/CAtlModule::AddCommonRGSReplacements.md)|重写此方法添加参数ATL注册表组件\(管理员\)替换映射。|  
|[CAtlModule::AddTermFunc](../Topic/CAtlModule::AddTermFunc.md)|当模块终止时，添加将名为的新功能。|  
|[CAtlModule::GetGITPtr](../Topic/CAtlModule::GetGITPtr.md)|返回全局接口指针。|  
|[CAtlModule::GetLockCount](../Topic/CAtlModule::GetLockCount.md)|返回锁计数。|  
|[CAtlModule::Lock](../Topic/CAtlModule::Lock.md)|增加锁计数。|  
|[CAtlModule::Term](../Topic/CAtlModule::Term.md)|释放所有数据成员。|  
|[CAtlModule::Unlock](../Topic/CAtlModule::Unlock.md)|减少锁计数。|  
|[CAtlModule::UpdateRegistryFromResourceD](../Topic/CAtlModule::UpdateRegistryFromResourceD.md)|运行在一指定资源中包含的脚本注册或注销对象。|  
|[CAtlModule::UpdateRegistryFromResourceDHelper](../Topic/CAtlModule::UpdateRegistryFromResourceDHelper.md)|此方法由 `UpdateRegistryFromResourceD` 调用执行注册表更新。|  
|[CAtlModule::UpdateRegistryFromResourceS](../Topic/CAtlModule::UpdateRegistryFromResourceS.md)|运行在一指定资源中包含的脚本注册或注销对象。  此方法与ATL注册表元素静态链接。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAtlModule::m\_libid](../Topic/CAtlModule::m_libid.md)|包含当前模块的GUID。|  
|[CAtlModule::m\_pGIT](../Topic/CAtlModule::m_pGIT.md)|对全局接口表的指针。|  
  
## 备注  
 [CAtlDllModuleT选件类](../../atl/reference/catldllmodulet-class.md)使用此选件类，[CAtlExeModuleT选件类](../../atl/reference/catlexemodulet-class.md)，因此，提供的 [CAtlServiceModuleT选件类](../../atl/reference/catlservicemodulet-class.md) 为DLL应用程序、EXE应用程序和Windows服务支持，分别。  
  
 有关ATL的模块的更多信息，请参见 [ATL模块选件类](../../atl/atl-module-classes.md)。  
  
 此选件类替换为使用ATL的早期版本的过时 [CComModule选件类](../../atl/reference/ccommodule-class.md)。  
  
## 继承层次结构  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 `CAtlModule`  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)   
 [注册表组件（注册器）](../../atl/atl-registry-component-registrar.md)