---
title: "FactoryCache 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::FactoryCache"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FactoryCache 结构"
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# FactoryCache 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] 基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
struct FactoryCache;  
```  
  
## 备注  
 标识包含已注册的类或 COM 类工厂对象和值的位置 wrt。  
  
## 成员  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[FactoryCache::cookie 数据成员](../windows/factorycache-cookie-data-member.md)|标识包含已注册 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 类或 COM 对象的值和用于注销后对象。|  
|[FactoryCache::factory 数据成员](../windows/factorycache-factory-data-member.md)|向 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 或 COM 类工厂的点。|  
  
## 继承层次结构  
 `FactoryCache`  
  
## 要求  
 **标头:** module.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)