---
title: "CPrintInfo Structure | Microsoft Docs"
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
  - "CPrintInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrintInfo structure"
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPrintInfo Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

有关打印或打印预览工作的存储信息。  
  
## 语法  
  
```  
struct CPrintInfo  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPrintInfo::GetFromPage](../Topic/CPrintInfo::GetFromPage.md)|返回打印的第一页的数字。|  
|[CPrintInfo::GetMaxPage](../Topic/CPrintInfo::GetMaxPage.md)|返回文档的最后一页的数字。|  
|[CPrintInfo::GetMinPage](../Topic/CPrintInfo::GetMinPage.md)|返回文档的第一页的数字。|  
|[CPrintInfo::GetOffsetPage](../Topic/CPrintInfo::GetOffsetPage.md)|返回位于DocObject项目的第一页的数量。中打印一项合并的DocObject打印作业。|  
|[CPrintInfo::GetToPage](../Topic/CPrintInfo::GetToPage.md)|返回打印的最后一页的数字。|  
|[CPrintInfo::SetMaxPage](../Topic/CPrintInfo::SetMaxPage.md)|设置文档的最后一页的数字。|  
|[CPrintInfo::SetMinPage](../Topic/CPrintInfo::SetMinPage.md)|设置文档的第一页的数字。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CPrintInfo::m\_bContinuePrinting](../Topic/CPrintInfo::m_bContinuePrinting.md)|包含指示框架是否的标志应继续打印循环。|  
|[CPrintInfo::m\_bDirect](../Topic/CPrintInfo::m_bDirect.md)|包含指示文档是否的标志直接打印\(不显示打印对话框）。|  
|[CPrintInfo::m\_bDocObject](../Topic/CPrintInfo::m_bDocObject.md)|包含指示打印的文档是否的标志是DocObject。|  
|[CPrintInfo::m\_bPreview](../Topic/CPrintInfo::m_bPreview.md)|包含指示文档是否的标志中预览。|  
|[CPrintInfo::m\_dwFlags](../Topic/CPrintInfo::m_dwFlags.md)|指定DocObject打印操作。|  
|[CPrintInfo::m\_lpUserData](../Topic/CPrintInfo::m_lpUserData.md)|包含指向用户生成的结构。|  
|[CPrintInfo::m\_nCurPage](../Topic/CPrintInfo::m_nCurPage.md)|标识当前打印的页的数字。|  
|[CPrintInfo::m\_nJobNumber](../Topic/CPrintInfo::m_nJobNumber.md)|对于当前打印作业指定操作系统分配的作业号|  
|[CPrintInfo::m\_nNumPreviewPages](../Topic/CPrintInfo::m_nNumPreviewPages.md)|标识在预览窗口中显示的页的数量;1或2。|  
|[CPrintInfo::m\_nOffsetPage](../Topic/CPrintInfo::m_nOffsetPage.md)|在一个合并的DocObject打印作业指定特定DocObject的第一页的偏移量。|  
|[CPrintInfo::m\_pPD](../Topic/CPrintInfo::m_pPD.md)|包含指向用于打印对话框的 `CPrintDialog` 对象。|  
|[CPrintInfo::m\_rectDraw](../Topic/CPrintInfo::m_rectDraw.md)|指定定义当前可用页区域的矩形。|  
|[CPrintInfo::m\_strPageDesc](../Topic/CPrintInfo::m_strPageDesc.md)|包含页显示数字的格式字符串。|  
  
## 备注  
 `CPrintInfo` 是结构，并没有基类。  
  
 结构创建 `CPrintInfo` 对象时，都会打印或打印预览命令上选择并销毁它，当命令完成。  
  
 `CPrintInfo` 包含有关整体打印作业的信息，如页的大小打印和打印作业的当前状态\(例如，当前打印的页。  一些信息在一个关联的 [CPrintDialog](../../mfc/reference/cprintdialog-class.md) 对象中存储;此对象在打印对话框包含用户输入的值。  
  
 `CPrintInfo` 对象通过在结构和您的视图选件类之间期间晒印方法和使用交换信息在两者之间。  例如，结构通知视图选件类打印的文档的页通过赋值。`CPrintInfo`的 `m_nCurPage` 成员;视图选件类检索该值并执行指定的页面的实际打印。  
  
 另一个示例是文档的长度未知的情况下，直到打印。  在这种情况下，每次页，打印，视图为文档末尾为检查。  当末尾时，视图选件类设置 `CPrintInfo` 的 `m_bContinuePrinting` 成员访问 **FALSE**;此通知机制停止打印循环。  
  
 `CView` 的功能下面列出的“并查看的成员使用`CPrintInfo` ”。有关Microsoft基础选件类库提供的打印结构的更多信息，请参见 [Windows框架](../../mfc/frame-windows.md) 和 [文档\/视图结构](../../mfc/document-view-architecture.md) 和文章 [打印](../../mfc/printing.md) 和 [打印:多页文档](../../mfc/multipage-documents.md)。  
  
## 继承层次结构  
 `CPrintInfo`  
  
## 要求  
 **Header:** afxext.h  
  
## 请参阅  
 [MFC示例DIBLOOK](../../top/visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CView::OnBeginPrinting](../Topic/CView::OnBeginPrinting.md)   
 [CView::OnEndPrinting](../Topic/CView::OnEndPrinting.md)   
 [CView::OnEndPrintPreview](../Topic/CView::OnEndPrintPreview.md)   
 [CView::OnPrepareDC](../Topic/CView::OnPrepareDC.md)   
 [CView::OnPreparePrinting](../Topic/CView::OnPreparePrinting.md)   
 [CView::OnPrint](../Topic/CView::OnPrint.md)