---
title: "CAtlComModule Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAtlComModule"
  - "CAtlComModule"
  - "ATL::CAtlComModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlComModule class"
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CAtlComModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现一个COM服务器模块。  
  
## 语法  
  
```  
  
   class CAtlComModule :  
public _ATL_COM_MODULE  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAtlComModule::CAtlComModule](../Topic/CAtlComModule::CAtlComModule.md)|构造函数。|  
|[CAtlComModule::~CAtlComModule](../Topic/CAtlComModule::~CAtlComModule.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAtlComModule::RegisterServer](../Topic/CAtlComModule::RegisterServer.md)|调用此方法将更新每个对象的系统注册表中对象映射。|  
|[CAtlComModule::RegisterTypeLib](../Topic/CAtlComModule::RegisterTypeLib.md)|调用此方法注册类型库。|  
|[CAtlComModule::UnregisterServer](../Topic/CAtlComModule::UnregisterServer.md)|调用此方法以注销在对象映射的每个对象。|  
|[CAtlComModule::UnRegisterTypeLib](../Topic/CAtlComModule::UnRegisterTypeLib.md)|调用此方法以注册类型库。|  
  
## 备注  
 `CAtlComModule` 实现一个COM服务器模块，将客户端访问模块的元素。  
  
 此选件类替换为使用ATL的早期版本的过时 [CComModule](../../atl/reference/ccommodule-class.md) 选件类。  有关详细信息 [ATL模块选件类](../../atl/atl-module-classes.md) 参见。  
  
## 继承层次结构  
 [\_ATL\_COM\_MODULE](../Topic/_ATL_COM_MODULE.md)  
  
 `CAtlComModule`  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [\_ATL\_COM\_MODULE](../Topic/_ATL_COM_MODULE.md)   
 [Class Overview](../../atl/atl-class-overview.md)