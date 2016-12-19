---
title: "CSize Class | Microsoft Docs"
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
  - "CSize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSize class"
  - "维数"
  - "维数, MFC"
  - "SIZE"
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
caps.latest.revision: 20
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSize Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

与Windows [范围](http://msdn.microsoft.com/library/windows/desktop/dd145106) 结构，实现相对坐标或位置。  
  
## 语法  
  
```  
class CSize : public tagSIZE  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSize::CSize](../Topic/CSize::CSize.md)|构造 `CSize` 对象。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CSize::operator \-](../Topic/CSize::operator%20-.md)|将两个范围。|  
|[CSize::operator \!\=](../Topic/CSize::operator%20!=.md)|不相等性检查在 `CSize` 和范围之内。|  
|[CSize::operator \+](../Topic/CSize::operator%20+.md)|添加两个范围。|  
|[CSize::operator \+\=](../Topic/CSize::operator%20+=.md)|添加一个范围。`CSize`。|  
|[CSize::operator \-\=](../Topic/CSize::operator%20-=.md)|从 `CSize`减去范围。|  
|[CSize::operator \=\=](../Topic/CSize::operator%20==.md)|相等性检查在 `CSize` 和范围之内。|  
  
## 备注  
 此选件类从 **SIZE** 不要求。  这意味着可以在需要 **SIZE**，并 **SIZE** 结构的数据成员是 `CSize`的访问数据成员的参数的 `CSize`。  
  
 **SIZE** \(和 `CSize`\) **cx** 和 **cy** 成员是公共的。  此外，`CSize` 实现成员函数操作 **SIZE** 结构。  
  
> [!NOTE]
>  有关共享实用工具选件类的更多信息\(如 `CSize`\)，请参见 [共享选件类](../../atl-mfc-shared/atl-mfc-shared-classes.md)。  
  
## 继承层次结构  
 `tagSIZE`  
  
 `CSize`  
  
## 要求  
 **Header:** atltypes.h  
  
## 请参阅  
 [MFC MDI示例](../../top/visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRect Class](../../atl-mfc-shared/reference/crect-class.md)   
 [CPoint Class](../../atl-mfc-shared/reference/cpoint-class.md)