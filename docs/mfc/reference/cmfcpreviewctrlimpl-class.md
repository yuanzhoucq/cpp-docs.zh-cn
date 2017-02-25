---
title: "CMFCPreviewCtrlImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPreviewCtrlImpl"
  - "afxwin/CMFCPreviewCtrlImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPreviewCtrlImpl class"
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CMFCPreviewCtrlImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现在Shell提供的宿主窗口放置为丰富预览的窗口。  
  
## 语法  
  
```  
class CMFCPreviewCtrlImpl : public CWnd;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCPreviewCtrlImpl::~CMFCPreviewCtrlImpl](../Topic/CMFCPreviewCtrlImpl::~CMFCPreviewCtrlImpl.md)|析构预览控件对象。|  
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](../Topic/CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl.md)|构造预览控件对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCPreviewCtrlImpl::Create](../Topic/CMFCPreviewCtrlImpl::Create.md)|已重载。  调用丰富的预览处理程序创建Windows窗口。|  
|[CMFCPreviewCtrlImpl::Destroy](../Topic/CMFCPreviewCtrlImpl::Destroy.md)|调用丰富的预览处理程序，则需要损坏此控件。|  
|[CMFCPreviewCtrlImpl::Focus](../Topic/CMFCPreviewCtrlImpl::Focus.md)|为此控件设置输入焦点。|  
|[CMFCPreviewCtrlImpl::GetDocument](../Topic/CMFCPreviewCtrlImpl::GetDocument.md)|返回文档连接到此预览控件。|  
|[CMFCPreviewCtrlImpl::Redraw](../Topic/CMFCPreviewCtrlImpl::Redraw.md)|调用此控件绘制。|  
|[CMFCPreviewCtrlImpl::SetDocument](../Topic/CMFCPreviewCtrlImpl::SetDocument.md)|调用预览处理程序创建文档实现和预览控件之间的关系。|  
|[CMFCPreviewCtrlImpl::SetHost](../Topic/CMFCPreviewCtrlImpl::SetHost.md)|将此控件的新父级。|  
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](../Topic/CMFCPreviewCtrlImpl::SetPreviewVisuals.md)|调用丰富的预览处理程序，则需要设置丰富预览可视化内容。|  
|[CMFCPreviewCtrlImpl::SetRect](../Topic/CMFCPreviewCtrlImpl::SetRect.md)|将此控件的一个新的边框。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCPreviewCtrlImpl::DoPaint](../Topic/CMFCPreviewCtrlImpl::DoPaint.md)|调用框架呈现预览。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCPreviewCtrlImpl::m\_clrBackColor](../Topic/CMFCPreviewCtrlImpl::m_clrBackColor.md)|预览窗口的背景色。|  
|[CMFCPreviewCtrlImpl::m\_clrTextColor](../Topic/CMFCPreviewCtrlImpl::m_clrTextColor.md)|预览窗口中的文本颜色。|  
|[CMFCPreviewCtrlImpl::m\_font](../Topic/CMFCPreviewCtrlImpl::m_font.md)|字体用于显示在预览窗口中显示的文本。|  
|[CMFCPreviewCtrlImpl::m\_pDocument](../Topic/CMFCPreviewCtrlImpl::m_pDocument.md)|为内容在控件中预览的文档的指针。|  
  
## 备注  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)  
  
## 要求  
 **标头：**afxwin.h