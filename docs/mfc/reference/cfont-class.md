---
title: "CFont Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFont"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFont class"
  - "字体, MFC 类"
  - "GDI, font classes"
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CFont Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装Windows图形设备接口\(GDI\)字体并为操作字体提供成员函数。  
  
## 语法  
  
```  
class CFont : public CGdiObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CFont::CFont](../Topic/CFont::CFont.md)|构造 `CFont` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFont::CreateFont](../Topic/CFont::CreateFont.md)|初始化指定特性的 `CFont`。|  
|[CFont::CreateFontIndirect](../Topic/CFont::CreateFontIndirect.md)|初始化与 `LOGFONT` framework为特性的一 `CFont` 对象。|  
|[CFont::CreatePointFont](../Topic/CFont::CreatePointFont.md)|初始化具有指定的高度 `CFont`，这些点处的十分之几秒和字样。|  
|[CFont::CreatePointFontIndirect](../Topic/CFont::CreatePointFontIndirect.md)|和 `CreateFontIndirect`，但字体高度相同的点处的十分之几秒为单位而不是逻辑单元。|  
|[CFont::FromHandle](../Topic/CFont::FromHandle.md)|返回指向 `CFont` 对象，同时使Windows **HFONT**。|  
|[CFont::GetLogFont](../Topic/CFont::GetLogFont.md)|用有关逻辑字体的信息来加载 `LOGFONT` 附加到 `CFont` 对象。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CFont::operator HFONT](../Topic/CFont::operator%20HFONT.md)|返回Windows GDI字体处理附加到 `CFont` 对象。|  
  
## 备注  
 若要使用 `CFont` 对象，构造一个 `CFont` 对象和其他Windows字体更改为其与 [CreateFont](../Topic/CFont::CreateFont.md)、 [CreateFontIndirect](../Topic/CFont::CreateFontIndirect.md)、 [CreatePointFont](../Topic/CFont::CreatePointFont.md)或 [CreatePointFontIndirect](../Topic/CFont::CreatePointFontIndirect.md)，然后使用对象的成员函数操纵字体。  
  
 因为它们自动执行，字体的高度将磅为逻辑单元 `CreatePointFont` 和 `CreatePointFontIndirect` 函数比 `CreateFont` 或 `CreateFontIndirect` 通常很方便。  
  
 有关 `CFont`的更多信息，请参见 [图形对象](../../mfc/graphic-objects.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CFont`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC示例HIERSVR](../../top/visual-cpp-samples.md)   
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)