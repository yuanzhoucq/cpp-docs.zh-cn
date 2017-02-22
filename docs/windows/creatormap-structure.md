---
title: "CreatorMap 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::CreatorMap"
  - "implements/Microsoft::WRL::Details::CreatorMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreatorMap 结构"
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# CreatorMap 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] 基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
struct CreatorMap;  
```  
  
## 备注  
 包含有关的信息初始化，并取消注册对象。  
  
 CreatorMap主题包含以下信息：  
  
-   如何初始化，并取消注册对象。  
  
-   根据如何传统 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 激活 COM 或工厂比较数据。  
  
-   有关缓存工厂的信息和服务器名称接口。  
  
## 成员  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CreatorMap::activationId 数据成员](../windows/creatormap-activationid-data-member.md)|表示由经典 COM 类 ID 或[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 名称标识的对象 ID。|  
|[CreatorMap::factoryCache 数据成员](../windows/creatormap-factorycache-data-member.md)|存储指向 CreatorMap Factory 缓存。|  
|[CreatorMap::factoryCreator 数据成员](../windows/creatormap-factorycreator-data-member.md)|创建指定的 CreatorMap 的工厂。|  
|[CreatorMap::serverName 数据成员](../windows/creatormap-servername-data-member.md)|为 CreatorMap 存储服务器名称。|  
  
## 继承层次结构  
 `CreatorMap`  
  
## 要求  
 **标头:** module.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)