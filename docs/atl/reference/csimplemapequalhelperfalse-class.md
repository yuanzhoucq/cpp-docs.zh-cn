---
title: "CSimpleMapEqualHelperFalse Class | Microsoft Docs"
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
  - "ATL::CSimpleMapEqualHelperFalse"
  - "CSimpleMapEqualHelperFalse"
  - "ATL.CSimpleMapEqualHelperFalse"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleMapEqualHelperFalse class"
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleMapEqualHelperFalse Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是 [CSimpleMap](../../atl/reference/csimplemap-class.md) 选件类的一个帮助器。  
  
## 语法  
  
```  
  
template < class TKey, class TVal > class CSimpleMapEqualHelperFalse  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSimpleMapEqualHelperFalse::IsEqualKey](../Topic/CSimpleMapEqualHelperFalse::IsEqualKey.md)|（静态）测试相等性的全部密钥。|  
|[CSimpleMapEqualHelperFalse::IsEqualValue](../Topic/CSimpleMapEqualHelperFalse::IsEqualValue.md)|（静态）返回false。|  
  
## 备注  
 此特征选件类是互补对于 `CSimpleMap` 选件类。  它用于比较在 `CSimpleMap` 对象包含的两个元素，专门两个值元素或两个关键元素提供方法。  
  
 值进行比较始终返回false，此外，此外，将调用变量的 `ATLASSERT` 错误，则引用。  在相等测试的情况下未充分定义，此选件类允许包含键\/值对映射对对于大多数方法都将正确运行，但failed with取决于比较例如 [CSimpleMap::FindVal](../Topic/CSimpleMap::FindVal.md)的方法的显式定义的方式。  
  
## 要求  
 **Header:** atlsimpcoll.h  
  
## 请参阅  
 [CSimpleMapEqualHelper Class](../../atl/reference/csimplemapequalhelper-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)