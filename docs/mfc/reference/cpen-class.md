---
title: "CPen Class | Microsoft Docs"
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
  - "HPEN"
  - "CPen"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPen class"
  - "HPEN"
  - "钢笔, MFC"
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPen Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装Windows图形设备接口\(GDI\)钢笔。  
  
## 语法  
  
```  
class CPen : public CGdiObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CPen::CPen](../Topic/CPen::CPen.md)|构造 `CPen` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPen::CreatePen](../Topic/CPen::CreatePen.md)|使用指定的样式、宽度和画笔属性创建一个逻辑化妆提供或几何形状钢笔，并将它附加到 `CPen` 对象。|  
|[CPen::CreatePenIndirect](../Topic/CPen::CreatePenIndirect.md)|在给定的样式、宽度和颜色创建一个钢笔在 [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) 结构，并将它附加到 `CPen` 对象。|  
|[CPen::FromHandle](../Topic/CPen::FromHandle.md)|返回指向 `CPen` 对象，同时使Windows `HPEN`。|  
|[CPen::GetExtLogPen](../Topic/CPen::GetExtLogPen.md)|获取 [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711) 基础结构。|  
|[CPen::GetLogPen](../Topic/CPen::GetLogPen.md)|获取 [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) 基础结构。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CPen::operator HPEN](../Topic/CPen::operator%20HPEN.md)|返回Windows处理附加到 `CPen` 对象。|  
  
## 备注  
 有关使用 `CPen`的更多信息，请参见 [图形对象](../../mfc/graphic-objects.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPen`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CBrush Class](../../mfc/reference/cbrush-class.md)