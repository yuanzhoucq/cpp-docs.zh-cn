---
title: "CPalette Class | Microsoft Docs"
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
  - "CPalette"
  - "HPALETTE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "调色板, MFC"
  - "CPalette class"
  - "HPALETTE"
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPalette Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装Windows调色板。  
  
## 语法  
  
```  
class CPalette : public CGdiObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CPalette::CPalette](../Topic/CPalette::CPalette.md)|构造 `CPalette` 对象未附加的Windows调色板。  才能使用，必须初始化与之一的 `CPalette` 对象初始化成员函数它。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPalette::AnimatePalette](../Topic/CPalette::AnimatePalette.md)|替换在 `CPalette` 标识的对象逻辑调色板的项。  因为Windows立即，映射新的项添加到系统调色板应用程序不必更新其工作区。|  
|[CPalette::CreateHalftonePalette](../Topic/CPalette::CreateHalftonePalette.md)|创建设备上下文的一个半音调色板并将它附加到 `CPalette` 对象。|  
|[CPalette::CreatePalette](../Topic/CPalette::CreatePalette.md)|创建一个Windows调色板并将它附加到 `CPalette` 对象。|  
|[CPalette::FromHandle](../Topic/CPalette::FromHandle.md)|返回指向 `CPalette` 对象，同时使处理Windows调色板对象。|  
|[CPalette::GetEntryCount](../Topic/CPalette::GetEntryCount.md)|检索调色板项的数目在逻辑调色板的。|  
|[CPalette::GetNearestPaletteIndex](../Topic/CPalette::GetNearestPaletteIndex.md)|返回项的索引在最匹配一种颜色值的逻辑调色板的。|  
|[CPalette::GetPaletteEntries](../Topic/CPalette::GetPaletteEntries.md)|检索调色板项的范围在逻辑调色板的。|  
|[CPalette::ResizePalette](../Topic/CPalette::ResizePalette.md)|更改项的指定数量的 `CPalette` 对象指定的逻辑调色板的大小。|  
|[CPalette::SetPaletteEntries](../Topic/CPalette::SetPaletteEntries.md)|设置RGB颜色值和标志。项的范围在逻辑调色板。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CPalette::operator HPALETTE](../Topic/CPalette::operator%20HPALETTE.md)|返回 `HPALETTE` 附加到 `CPalette`。|  
  
## 备注  
 调色板提供应用程序和颜色输出设备之间的接口\(例如显示设备）。  接口允许应用程序利用输出设备的颜色功能，而无需严重影响其他应用程序显示的颜色。  Windows使用应用程序的逻辑调色板\(需要的颜色列表\)和定义可用的颜色\)的系统调色板\(确定要使用的颜色。  
  
 `CPalette` 对象用于操作对象引用的调色板提供成员函数。  构造 `CPalette` 对象并使用其成员函数创建物理调色板，图形设备接口\(GDI\)对象并操作其项和其他属性。  
  
 有关使用 `CPalette`的更多信息，请参见 [图形对象](../../mfc/graphic-objects.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPalette`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC示例DIBLOOK](../../top/visual-cpp-samples.md)   
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPalette::GetPaletteEntries](../Topic/CPalette::GetPaletteEntries.md)   
 [CPalette::SetPaletteEntries](../Topic/CPalette::SetPaletteEntries.md)