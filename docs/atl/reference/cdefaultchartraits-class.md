---
title: "CDefaultCharTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDefaultCharTraits"
  - "ATL::CDefaultCharTraits<T>"
  - "ATL.CDefaultCharTraits"
  - "ATL.CDefaultCharTraits<T>"
  - "ATL::CDefaultCharTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDefaultCharTraits class"
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CDefaultCharTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类为将在大写和小写之间的字符提供两个静态函数。  
  
## 语法  
  
```  
  
      template <  
   typename T  
>  
class CDefaultCharTraits  
```  
  
#### 参数  
 `T`  
 要存储在集合中的数据的类型。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDefaultCharTraits::CharToLower](../Topic/CDefaultCharTraits::CharToLower.md)|（静态）调用此函数将字符转换为大写。|  
|[CDefaultCharTraits::CharToUpper](../Topic/CDefaultCharTraits::CharToUpper.md)|（静态）调用此函数将字符转换为小写。|  
  
## 备注  
 此选件类提供选件类使用 [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)的功能。  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)