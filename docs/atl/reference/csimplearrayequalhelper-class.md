---
title: "CSimpleArrayEqualHelper Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSimpleArrayEqualHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleArrayEqualHelper class"
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CSimpleArrayEqualHelper Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是 [CSimpleArray](../../atl/reference/csimplearray-class.md) 选件类的一个帮助器。  
  
## 语法  
  
```  
  
      template <  
   class T   
>  
class CSimpleArrayEqualHelper  
```  
  
#### 参数  
 `T`  
 派生类。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSimpleArrayEqualHelper::IsEqual](../Topic/CSimpleArrayEqualHelper::IsEqual.md)|（静态）测试相等的两个 `CSimpleArray` 对象元素。|  
  
## 备注  
 此特征选件类是互补对于 `CSimpleArray` 选件类。  它用于比较在 `CSimpleArray` 对象存储的两个组件提供方法。  默认情况下，使用 **operator\=\(\)**，元素进行比较，所以，但是，如果数组包含缺少其相等运算符的复杂数据类型，则需要重写此选件类。  
  
## 要求  
 **Header:** atlsimpcoll.h  
  
## 请参阅  
 [CSimpleArray Class](../../atl/reference/csimplearray-class.md)   
 [CSimpleArrayEqualHelperFalse Class](../../atl/reference/csimplearrayequalhelperfalse-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)