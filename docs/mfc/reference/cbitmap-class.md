---
title: "CBitmap Class | Microsoft Docs"
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
  - "CBitmap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBitmap class"
  - "drawing, 工具"
  - "GDI bitmap"
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBitmap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装Windows图形设备接口\(GDI\)位图并提供成员函数操作位图。  
  
## 语法  
  
```  
class CBitmap : public CGdiObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CBitmap::CBitmap](../Topic/CBitmap::CBitmap.md)|构造 `CBitmap` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CBitmap::CreateBitmap](../Topic/CBitmap::CreateBitmap.md)|初始化具有指定的宽度、高度和位组合的设备相关的内存位图的对象。|  
|[CBitmap::CreateBitmapIndirect](../Topic/CBitmap::CreateBitmapIndirect.md)|初始化位图的对象与 **BITMAP** 结构\(如果指定了\)生成的宽度、高度和位组合。|  
|[CBitmap::CreateCompatibleBitmap](../Topic/CBitmap::CreateCompatibleBitmap.md)|初始化使用位图的对象，以使其与指定的设备兼容。|  
|[CBitmap::CreateDiscardableBitmap](../Topic/CBitmap::CreateDiscardableBitmap.md)|初始化与指定的设备兼容的一discardable位图的对象。|  
|[CBitmap::FromHandle](../Topic/CBitmap::FromHandle.md)|返回指向 `CBitmap` 对象，同时使处理Windows `HBITMAP` 位图。|  
|[CBitmap::GetBitmap](../Topic/CBitmap::GetBitmap.md)|用有关位图的信息来加载一 **BITMAP** 结构。|  
|[CBitmap::GetBitmapBits](../Topic/CBitmap::GetBitmapBits.md)|复制指定的位图的位到指定缓冲区。|  
|[CBitmap::GetBitmapDimension](../Topic/CBitmap::GetBitmapDimension.md)|返回位图的宽度和高度。  该高度和宽度假定由 [SetBitmapDimension](../Topic/CBitmap::SetBitmapDimension.md) 成员函数之前设置。|  
|[CBitmap::LoadBitmap](../Topic/CBitmap::LoadBitmap.md)|通过填写命名位图资源从应用程序的可执行文件和附加位图初始化对象到对象。|  
|[CBitmap::LoadMappedBitmap](../Topic/CBitmap::LoadMappedBitmap.md)|加载位图和映射颜色设置为当前系统颜色。|  
|[CBitmap::LoadOEMBitmap](../Topic/CBitmap::LoadOEMBitmap.md)|通过加载预定义的Windows位图和附加位图初始化对象到对象。|  
|[CBitmap::SetBitmapBits](../Topic/CBitmap::SetBitmapBits.md)|将位图的位到指定的位值。|  
|[CBitmap::SetBitmapDimension](../Topic/CBitmap::SetBitmapDimension.md)|分配宽度和高度到0.1个单位的位图。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CBitmap::operator HBITMAP](../Topic/CBitmap::operator%20HBITMAP.md)|返回Windows处理附加到 `CBitmap` 对象。|  
  
## 备注  
 若要使用 `CBitmap` 对象，请构造对象，将位图句柄它使用一个初始化成员函数，然后调用对象的成员函数。  
  
 有关使用图形对象的更多信息\(如 `CBitmap`，请参见 [图形对象](../../mfc/graphic-objects.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBitmap`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC MDI示例](../../top/visual-cpp-samples.md)   
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)