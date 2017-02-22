---
title: "Security Global Functions | Microsoft Docs"
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
  - "ACL object global functions"
  - "security IDs [C++]"
  - "SIDs [C++], modifying SID objects"
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# Security Global Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些功能提供用于修改的SID和ACL对象支持。  
  
> [!IMPORTANT]
>  下表中列出的函数不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
|||  
|-|-|  
|[AtlGetDacl](../Topic/AtlGetDacl.md)|调用该函数检索指定对象中的自由访问控制列表\(acl\) \(DACL\)信息。|  
|[AtlSetDacl](../Topic/AtlSetDacl.md)|调用此函数将指定对象中的自由访问控制列表\(acl\) \(DACL\)信息。|  
|[AtlGetGroupSid](../Topic/AtlGetGroupSid.md)|调用该函数检索对象组安全标识符\(SID）。|  
|[AtlSetGroupSid](../Topic/AtlSetGroupSid.md)|调用此函数将对象的组安全标识符\(SID）。|  
|[AtlGetOwnerSid](../Topic/AtlGetOwnerSid.md)|调用该函数检索对象的所有者安全标识符\(SID）。|  
|[AtlSetOwnerSid](../Topic/AtlSetOwnerSid.md)|调用此函数将对象的所有者安全标识符\(SID）。|  
|[AtlGetSacl](../Topic/AtlGetSacl.md)|调用该函数检索指定对象中的系统访问控制列表\(acl\) \(SACL\)信息。|  
|[AtlSetSacl](../Topic/AtlSetSacl.md)|调用此函数将指定对象中的系统访问控制列表\(acl\) \(SACL\)信息。|  
|[AtlGetSecurityDescriptor](../Topic/AtlGetSecurityDescriptor.md)|调用此函数检索特定对象的安全说明符。|  
  
## 请参阅  
 [函数](../../atl/reference/atl-functions.md)