---
title: "CComModule Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComModule class"
  - "DLL modules [C++], ATL"
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CComModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

自ATL 7.0，`CComModule` 弃用的:有关详细信息 [ATL模块选件类](../../atl/atl-module-classes.md) 参见。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
class CComModule : public _ATL_MODULE  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComModule::GetClassObject](../Topic/CComModule::GetClassObject.md)|创建一个指定的CLSID的对象。  仅用于 DLLs。|  
|[CComModule::GetModuleInstance](../Topic/CComModule::GetModuleInstance.md)|返回 `m_hInst`。|  
|[CComModule::GetResourceInstance](../Topic/CComModule::GetResourceInstance.md)|返回 `m_hInstResource`。|  
|[CComModule::GetTypeLibInstance](../Topic/CComModule::GetTypeLibInstance.md)|返回 `m_hInstTypeLib`。|  
|[CComModule::Init](../Topic/CComModule::Init.md)|初始化数据成员。|  
|[CComModule::RegisterClassHelper](../Topic/CComModule::RegisterClassHelper.md)|在系统注册表输入对象的标准选件类注册。|  
|[CComModule::RegisterClassObjects](../Topic/CComModule::RegisterClassObjects.md)|注册选件类对象。  仅对EXE。|  
|[CComModule::RegisterServer](../Topic/CComModule::RegisterServer.md)|更新每个对象的系统注册表中对象映射。|  
|[CComModule::RegisterTypeLib](../Topic/CComModule::RegisterTypeLib.md)|注册类型库。|  
|[CComModule::RevokeClassObjects](../Topic/CComModule::RevokeClassObjects.md)|取消选件类对象。  仅对EXE。|  
|[CComModule::Term](../Topic/CComModule::Term.md)|释放数据成员。|  
|[CComModule::UnregisterClassHelper](../Topic/CComModule::UnregisterClassHelper.md)|从系统注册表中移除对象的标准选件类注册。|  
|[CComModule::UnregisterServer](../Topic/CComModule::UnregisterServer.md)|注销在对象映射的每个对象。|  
|[CComModule::UpdateRegistryClass](../Topic/CComModule::UpdateRegistryClass.md)|注册或注销对象的标准选件类注册。|  
|[CComModule::UpdateRegistryFromResourceD](../Topic/CComModule::UpdateRegistryFromResourceD.md)|运行在一指定资源中包含的脚本注册或注销对象。|  
|[CComModule::UpdateRegistryFromResourceS](../Topic/CComModule::UpdateRegistryFromResourceS.md)|ATL注册表元素的静态链接。  运行在一指定资源中包含的脚本注册或注销对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComModule::m\_csObjMap](../Topic/CComModule::m_csObjMap.md)|ensures同步访问对象映射信息的访问。|  
|[CComModule::m\_csTypeInfoHolder](../Topic/CComModule::m_csTypeInfoHolder.md)|ensures同步到类型库信息的访问。|  
|[CComModule::m\_csWindowCreate](../Topic/CComModule::m_csWindowCreate.md)|ensures同步对"窗口"创建时和静态数据的访问使用的选件类信息。|  
|[CComModule::m\_hInst](../Topic/CComModule::m_hInst.md)|包含处理对于模块实例。|  
|[CComModule::m\_hInstResource](../Topic/CComModule::m_hInstResource.md)|默认情况下，包含句柄模块实例。|  
|[CComModule::m\_hInstTypeLib](../Topic/CComModule::m_hInstTypeLib.md)|默认情况下，包含句柄模块实例。|  
|[CComModule::m\_pObjMap](../Topic/CComModule::m_pObjMap.md)|指向模块实例维护的对象映射。|  
  
## 备注  
  
> [!NOTE]
>  此选件类已弃用，因此，生成ATL代码向导现在使用 [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) 和 [CAtlModule](../../atl/reference/catlmodule-class.md) 派生类。  请参见 [ATL模块选件类](../../atl/atl-module-classes.md) 有关更多信息。  下面的信息函数使用ATL的早期版本创建的应用程序中。  `CComModule` 向后仍作为ATL的部分功能。  
  
 `CComModule` 实现一个COM服务器模块，将客户端访问模块的元素。  `CComModule` 支持DLL \(过程\)和EXE \(本地\)模块。  
  
 `CComModule` 实例使用对象映射维护一组选件类对象定义。  此对象映射实现为数组 `_ATL_OBJMAP_ENTRY` 结构，并包含信息为:  
  
-   输入和移除对象声明在系统注册表。  
  
-   实例化的对象。选件类工厂。  
  
-   建立客户端和根对象之间的通信元素。  
  
-   执行选件类对象的生存期管理。  
  
 当您运行ATL COM AppWizard时，向导自动生成 `_Module`、 `CComModule` 全局实例或其派生的选件类。  有关ATL项目向导的更多信息，请参见文章 [创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)。  
  
 除了 `CComModule`外，ATL提供 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)，实现EXE和Windows服务的一个单元模型模块。  用于在多个单元时，创建对象从 `CComAutoThreadModule` 则应从派生该模块。  
  
## 继承层次结构  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CComModule`  
  
## 要求  
 `Header:` atlbase.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)