---
title: "CBrush Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "画笔, CBrush class"
  - "CBrush class"
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CBrush Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装Windows图形设备接口\(GDI\)画笔。  
  
## 语法  
  
```  
class CBrush : public CGdiObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CBrush::CBrush](../Topic/CBrush::CBrush.md)|构造 `CBrush` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CBrush::CreateBrushIndirect](../Topic/CBrush::CreateBrushIndirect.md)|初始化与 [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) 结构指定的样式、颜色和模式的画笔。|  
|[CBrush::CreateDIBPatternBrush](../Topic/CBrush::CreateDIBPatternBrush.md)|初始化一个设备无关位图\(dib\)与指定模式的画笔\(DIB）。|  
|[CBrush::CreateHatchBrush](../Topic/CBrush::CreateHatchBrush.md)|初始化具有指定的阴影的模式和颜色的画笔。|  
|[CBrush::CreatePatternBrush](../Topic/CBrush::CreatePatternBrush.md)|初始化使用位图指定模式的画笔。|  
|[CBrush::CreateSolidBrush](../Topic/CBrush::CreateSolidBrush.md)|初始化使用指定的纯色的画笔。|  
|[CBrush::CreateSysColorBrush](../Topic/CBrush::CreateSysColorBrush.md)|创建是默认系统颜色的画笔。|  
|[CBrush::FromHandle](../Topic/CBrush::FromHandle.md)|返回指向 `CBrush` 对象，同时使处理Windows `HBRUSH` 对象。|  
|[CBrush::GetLogBrush](../Topic/CBrush::GetLogBrush.md)|获取 [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) 结构。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CBrush::operator HBRUSH](../Topic/CBrush::operator%20HBRUSH.md)|返回Windows处理附加到 `CBrush` 对象。|  
  
## 备注  
 若要使用 `CBrush` 对象，请构造 `CBrush` 对象并将其传递给需要一个画笔的所有 `CDC` 成员函数。  
  
 画笔可以修复，阴影或模式。  
  
 有关 `CBrush`的更多信息，请参见 [图形对象](../../mfc/graphic-objects.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBrush`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC示例PROPDLG](../../top/visual-cpp-samples.md)   
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CBitmap Class](../../mfc/reference/cbitmap-class.md)   
 [CDC 类](../../mfc/reference/cdc-class.md)