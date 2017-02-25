---
title: "CSimpleMapEqualHelper Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSimpleMapEqualHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleMapEqualHelper class"
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CSimpleMapEqualHelper Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是 [CSimpleMap](../../atl/reference/csimplemap-class.md) 选件类的一个帮助器。  
  
## 语法  
  
```  
  
      template <  
   class TKey,  
   class TVal   
>  
class CSimpleMapEqualHelper  
```  
  
#### 参数  
 `TKey`  
 关键元素。  
  
 `TVal`  
 值元素。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSimpleMapEqualHelper::IsEqualKey](../Topic/CSimpleMapEqualHelper::IsEqualKey.md)|（静态）测试相等性的全部密钥。|  
|[CSimpleMapEqualHelper::IsEqualValue](../Topic/CSimpleMapEqualHelper::IsEqualValue.md)|（静态）测试两个值是否相等。|  
  
## 备注  
 此特征选件类是互补对于 `CSimpleMap` 选件类。  它用于比较两个 `CSimpleMap` 对象元素的方法\(特别是，键和值的元素\)相等的。  默认情况下，使用 `operator==()`，键和值进行比较，所以，但是，如果映射包含缺少其相等运算符的复杂数据类型，此选件类可以重写提供多余的需的功能。  
  
## 要求  
 **标头:** atlsimpcoll.h  
  
## 请参阅  
 [CSimpleMapEqualHelperFalse Class](../../atl/reference/csimplemapequalhelperfalse-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)