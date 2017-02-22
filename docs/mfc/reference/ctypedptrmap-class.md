---
title: "CTypedPtrMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTypedPtrMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTypedPtrMap class"
  - "映射"
  - "pointer maps"
  - "template classes, CTypedPtrMap class"
  - "type-safe collections"
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CTypedPtrMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于指针地图选件类提供类型安全的“包装” `CMapPtrToPtr`、 `CMapPtrToWord`、 `CMapWordToPtr`和 `CMapStringToPtr`的对象。  
  
## 语法  
  
```  
template< class BASE_CLASS, class KEY, class VALUE >  
class CTypedPtrMap : public BASE_CLASS  
```  
  
#### 参数  
 `BASE_CLASS`  
 类型化指针映射选件类的基类;必须是指向映射选件类\(`CMapPtrToPtr`、 `CMapPtrToWord`、 `CMapWordToPtr`或 `CMapStringToPtr`）。  
  
 `KEY`  
 作为键使用对象的选件类为映射。  
  
 `VALUE`  
 在映射中存储的对象选件类。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CTypedPtrMap::GetNextAssoc](../Topic/CTypedPtrMap::GetNextAssoc.md)|获取重复的下一个元素。|  
|[CTypedPtrMap::Lookup](../Topic/CTypedPtrMap::Lookup.md)|返回基于 `VALUE`的 `KEY`。|  
|[CTypedPtrMap::RemoveKey](../Topic/CTypedPtrMap::RemoveKey.md)|移除项指定的元素。|  
|[CTypedPtrMap::SetAt](../Topic/CTypedPtrMap::SetAt.md)|将元素插入到映射中;，如果找到，替换现有元素匹配键。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CTypedPtrMap::operator](../Topic/CTypedPtrMap::operator.md)|将元素插入到映射中。|  
  
## 备注  
 当您使用 `CTypedPtrMap`时，类型检查计算机帮助的C\+\+消除不匹配的指针类型引起的错误。  
  
 由于所有 `CTypedPtrMap` 函数内联，该模板的使用不显着影响您的代码的大小或速度。  
  
 有关使用 `CTypedPtrMap`的更多信息，请参见位于 [集合](../../mfc/collections.md) 和 [基于模板的选件类](../../mfc/template-based-classes.md)。  
  
## 继承层次结构  
 `BASE_CLASS`  
  
 `CTypedPtrMap`  
  
## 要求  
 **Header:** afxtempl.h  
  
## 请参阅  
 [MFC示例集合](../../top/visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMapPtrToPtr Class](../../mfc/reference/cmapptrtoptr-class.md)   
 [CMapPtrToWord Class](../../mfc/reference/cmapptrtoword-class.md)   
 [CMapWordToPtr Class](../../mfc/reference/cmapwordtoptr-class.md)   
 [CMapStringToPtr Class](../../mfc/reference/cmapstringtoptr-class.md)