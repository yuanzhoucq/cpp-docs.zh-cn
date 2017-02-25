---
title: "Registry and TypeLib Global Functions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RegistryDataExchange function, 全局函数"
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# Registry and TypeLib Global Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些功能提供用于加载和注册类型支持库。  
  
> [!IMPORTANT]
>  在下表中列出的函数不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
|||  
|-|-|  
|[AtlRegisterTypeLib](../Topic/AtlRegisterTypeLib.md)|此功能称为注册类型库。|  
|[AtlUnRegisterTypeLib](../Topic/AtlUnRegisterTypeLib.md)|此功能称为取消注册类型库|  
|[AtlLoadTypeLib](../Topic/AtlLoadTypeLib.md)|此功能称为加载类型库。|  
|[AtlUpdateRegistryFromResourceD](../Topic/AtlUpdateRegistryFromResourceD.md)|此功能称为更新对种提供的资源的注册表。|  
|[RegistryDataExchange](../Topic/RegistryDataExchange.md)|此功能称为读取或写入，系统注册表。  调用 [注册表数据交换的宏](../../atl/reference/registry-data-exchange-macros.md)。|  
  
 在注册表的节点程序用于存储信息的这些功能控制。  
  
|||  
|-|-|  
|[AtlGetPerUserRegistration](../Topic/AtlGetPerUserRegistration.md)|检索应用程序是否重到 **HKEY\_CURRENT\_USER** \(**HKCU**\)节点的注册表访问方向。|  
|[AtlSetPerUserRegistration](../Topic/AtlSetPerUserRegistration.md)|设置应用程序是否重到 **HKEY\_CURRENT\_USER** \(**HKCU**\)节点的注册表访问方向。|  
  
## 请参阅  
 [函数](../../atl/reference/atl-functions.md)