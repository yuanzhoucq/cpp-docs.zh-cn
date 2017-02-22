---
title: "CStatic Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStatic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bitmaps, 显示"
  - "控件 [MFC], static"
  - "CStatic class"
  - "光标, 显示"
  - "enhanced metafiles"
  - "enhanced metafiles, 显示"
  - "图标, 显示"
  - "static controls"
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CStatic Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows静态控件的功能。  
  
## 语法  
  
```  
class CStatic : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CStatic::CStatic](../Topic/CStatic::CStatic.md)|构造 `CStatic` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CStatic::Create](../Topic/CStatic::Create.md)|创建Windows静态控件并将它附加到 `CStatic` 对象。|  
|[CStatic::DrawItem](../Topic/CStatic::DrawItem.md)|绘制一个所有者描述的静态控件的重写。|  
|[CStatic::GetBitmap](../Topic/CStatic::GetBitmap.md)|检索位图的处理之前设置与 [SetBitmap](../Topic/CStatic::SetBitmap.md)。|  
|[CStatic::GetCursor](../Topic/CStatic::GetCursor.md)|检索光标图像的句柄之前设置与 [SetCursor](../Topic/CStatic::SetCursor.md)。|  
|[CStatic::GetEnhMetaFile](../Topic/CStatic::GetEnhMetaFile.md)|检索该增强型图元文件的处理之前设置与 [SetEnhMetaFile](../Topic/CStatic::SetEnhMetaFile.md)。|  
|[CStatic::GetIcon](../Topic/CStatic::GetIcon.md)|检索图标句柄之前设置与 [SetIcon](../Topic/CStatic::SetIcon.md)。|  
|[CStatic::SetBitmap](../Topic/CStatic::SetBitmap.md)|指定在静态控件中显示的位图。|  
|[CStatic::SetCursor](../Topic/CStatic::SetCursor.md)|指定在静态控件中显示的光标图像。|  
|[CStatic::SetEnhMetaFile](../Topic/CStatic::SetEnhMetaFile.md)|指定在静态控件中显示的一个增强型图元文件。|  
|[CStatic::SetIcon](../Topic/CStatic::SetIcon.md)|指定在静态控件中显示的图标。|  
  
## 备注  
 静态控件显示文本字符串、框、矩形、图标、光标、位图、增强型图元文件。  它可用于标记，将或分隔其他控件包。  静态控件通常不接受输入而提供的输出;但是，则为;如果使用 **SS\_NOTIFY** 样式，创建了它可能会注意到其鼠标单击的父级。  
  
 创建静态控件在两个步骤。  首先，调用构造函数构造 `CStatic` 对象，然后调用 [创建](../Topic/CStatic::Create.md) 成员函数创建该静态控件并将其附加到 `CStatic` 对象。  
  
 如果要创建在对话框中的一 `CStatic` 对象\(通过对话框资源\)，自动销毁 `CStatic` 对象，当用户关闭对话框时。  
  
 如果在中创建的一 `CStatic` 对象，您可能还需要销毁它。  自动销毁。在窗口中的堆栈创建的 `CStatic` 对象。  使用 **new** 功能，如果要创建在堆的 `CStatic` 对象，则必须对对象的 **delete** 销毁它，当处理它。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatic`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)