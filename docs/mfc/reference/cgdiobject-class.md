---
title: "CGdiObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CGdiObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "画笔, base class for"
  - "CGdiObject class"
  - "字体, base class for"
  - "GDI 对象, base class for"
  - "调色板, base class for"
  - "钢笔, base class for"
  - "区域, base class for"
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CGdiObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为各种Windows图形设备接口\(GDI\)对象提供基类如位图、区域、画笔、钢笔、调色板和字体。  
  
## 语法  
  
```  
class CGdiObject : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CGdiObject::CGdiObject](../Topic/CGdiObject::CGdiObject.md)|构造 `CGdiObject` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CGdiObject::Attach](../Topic/CGdiObject::Attach.md)|附加到 `CGdiObject` 对象的一个Windows GDI对象。|  
|[CGdiObject::CreateStockObject](../Topic/CGdiObject::CreateStockObject.md)|检索处理某个Windows预定义的库存钢笔、画笔或字体。|  
|[CGdiObject::DeleteObject](../Topic/CGdiObject::DeleteObject.md)|从内存中删除释放附加到 `CGdiObject` 对象Windows GDI对象所有系统存储与对象。|  
|[CGdiObject::DeleteTempMap](../Topic/CGdiObject::DeleteTempMap.md)|删除 `FromHandle`创建的所有瞬态 `CGdiObject` 对象。|  
|[CGdiObject::Detach](../Topic/CGdiObject::Detach.md)|分离 `CGdiObject` 对象的一个Windows GDI对象并将处理返回到Windows GDI对象。|  
|[CGdiObject::FromHandle](../Topic/CGdiObject::FromHandle.md)|返回指向 `CGdiObject` 对象提供处理Windows GDI对象。|  
|[CGdiObject::GetObject](../Topic/CGdiObject::GetObject.md)|用描述附加的Windows GDI对象。`CGdiObject` 对象的数据填充缓冲区。|  
|[CGdiObject::GetObjectType](../Topic/CGdiObject::GetObjectType.md)|检索GDI对象的类型。|  
|[CGdiObject::GetSafeHandle](../Topic/CGdiObject::GetSafeHandle.md)|返回 `m_hObject`，除非 `this` 是，`NULL`，在 `NULL` 返回情况下。|  
|[CGdiObject::UnrealizeObject](../Topic/CGdiObject::UnrealizeObject.md)|重置画笔的原点或重置一个逻辑调色板。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CGdiObject::operator \!\=](../Topic/CGdiObject::operator%20!=.md)|GDI确定两个对象是否不逻辑上是相等。|  
|[CGdiObject::operator \=\=](../Topic/CGdiObject::operator%20==.md)|确定两个GDI对象是否是逻辑上相等。|  
|[CGdiObject::operator HGDIOBJ](../Topic/CGdiObject::operator%20HGDIOBJ.md)|检索 `HANDLE` 附加Windows GDI对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CGdiObject::m\_hObject](../Topic/CGdiObject::m_hObject.md)|包含 `HBITMAP`、 `HPALETTE`、 `HRGN`、 `HBRUSH`、 `HPEN`或 `HFONT` 的 `HANDLE` 附加到该对象。|  
  
## 备注  
 您从不直接创建 `CGdiObject`。  相反，您创建从其派生类之一的对象，例如 `CPen` 或 `CBrush`。  
  
 有关 `CGdiObject` 的更多信息，请参见 [图形对象](../../mfc/graphic-objects.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGdiObject`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CBitmap Class](../../mfc/reference/cbitmap-class.md)   
 [CBrush Class](../../mfc/reference/cbrush-class.md)   
 [CFont Class](../../mfc/reference/cfont-class.md)   
 [CPalette Class](../../mfc/reference/cpalette-class.md)   
 [CPen Class](../../mfc/reference/cpen-class.md)   
 [CRgn 类](../../mfc/reference/crgn-class.md)