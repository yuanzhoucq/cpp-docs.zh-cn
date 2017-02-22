---
title: "CSimpleArrayEqualHelperFalse Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CSimpleArrayEqualHelperFalse<T>"
  - "ATL::CSimpleArrayEqualHelperFalse"
  - "ATL.CSimpleArrayEqualHelperFalse"
  - "ATL::CSimpleArrayEqualHelperFalse<T>"
  - "CSimpleArrayEqualHelperFalse"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleArrayEqualHelperFalse class"
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CSimpleArrayEqualHelperFalse Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是 [CSimpleArray](../../atl/reference/csimplearray-class.md) 选件类的一个帮助器。  
  
## 语法  
  
```  
  
      template <  
   class T   
>   
class CSimpleArrayEqualHelperFalse  
```  
  
#### 参数  
 `T`  
 派生类。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSimpleArrayEqualHelperFalse::IsEqual](../Topic/CSimpleArrayEqualHelperFalse::IsEqual.md)|（静态）返回false。|  
  
## 备注  
 此特征选件类是补充到 `CSimpleArray` 选件类。  它始终返回false，此外，此外，将调用变量的 `ATLASSERT` 错误，则引用。  在相等测试的情况下未充分定义，此选件类允许数组包含元素对于大多数方法都将正确运行，但failed with取决于比较例如 [CSimpleArray::Find](../Topic/CSimpleArray::Find.md)的方法的显式定义的方式。  
  
## 要求  
 **Header:** atlsimpcoll.h  
  
## 请参阅  
 [CSimpleArrayEqualHelper Class](../../atl/reference/csimplearrayequalhelper-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)