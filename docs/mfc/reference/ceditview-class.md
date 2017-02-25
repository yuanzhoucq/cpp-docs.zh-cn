---
title: "CEditView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CEditView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEditView class"
  - "edit controls, 类"
  - "text editors"
  - "text editors, CEditView class"
  - "视图, 类"
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CEditView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

的视图选件类的类型提供Windows的功能编辑控件，并且可用于实现简单的文本编辑功能。  
  
## 语法  
  
```  
class CEditView : public CCtrlView  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CEditView::CEditView](../Topic/CEditView::CEditView.md)|构造对象类型 `CEditView`。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CEditView::FindText](../Topic/CEditView::FindText.md)|搜索文本内的字符串。|  
|[CEditView::GetBufferLength](../Topic/CEditView::GetBufferLength.md)|获取字符缓冲区的长度。|  
|[CEditView::GetEditCtrl](../Topic/CEditView::GetEditCtrl.md)|提供对 `CEditView` 对象的 `CEdit` 部分\(Windows编辑控件）。|  
|[CEditView::GetPrinterFont](../Topic/CEditView::GetPrinterFont.md)|检索当前打印机字体。|  
|[CEditView::GetSelectedText](../Topic/CEditView::GetSelectedText.md)|检索当前文本选择。|  
|[CEditView::LockBuffer](../Topic/CEditView::LockBuffer.md)|锁定缓冲区。|  
|[CEditView::PrintInsideRect](../Topic/CEditView::PrintInsideRect.md)|呈现在特定矩形内的文本。|  
|[CEditView::SerializeRaw](../Topic/CEditView::SerializeRaw.md)|对磁盘的 `CEditView` 对象作为原始的文本。|  
|[CEditView::SetPrinterFont](../Topic/CEditView::SetPrinterFont.md)|设置新的打印机字体。|  
|[CEditView::SetTabStops](../Topic/CEditView::SetTabStops.md)|设置屏幕显示和打印的制表位。|  
|[CEditView::UnlockBuffer](../Topic/CEditView::UnlockBuffer.md)|打开缓冲区。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CEditView::OnFindNext](../Topic/CEditView::OnFindNext.md)|文本字符串中查找下一个匹配项。|  
|[CEditView::OnReplaceAll](../Topic/CEditView::OnReplaceAll.md)|用新的字符串替换特定字符串的所有匹配项。|  
|[CEditView::OnReplaceSel](../Topic/CEditView::OnReplaceSel.md)|替换当前选择。|  
|[CEditView::OnTextNotFound](../Topic/CEditView::OnTextNotFound.md)|调用，则查找操作不能与任何其他文本。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CEditView::dwStyleDefault](../Topic/CEditView::dwStyleDefault.md)|类型 **CEditView.**对象的默认样式|  
  
## 备注  
 `CEditView` 选件类提供以下附加功能:  
  
-   打印。  
  
-   查找并替换。  
  
 由于选件类 `CEditView` 是选件类 `CView`的派生对象，`CEditView` 可用于选件类的对象文档和文档模板。  
  
 每个 `CEditView` 控件的文本在其自己的全局内存对象保留。  应用程序可以具有任意数量的 `CEditView` 对象。  
  
 创建类型 `CEditView` 对象，如果需要列出了所添加的函数的一个编辑器窗口中，或者，如果需要简单的文本编辑功能。  `CEditView` 对象可以占用窗口的整个工作区。  从 `CEditView` 派生您的选件类添加或修改了基本功能，或者声明可以添加到文档模板的选件类。  
  
 选件类 `CEditView` 处理的默认实现以下命令: **ID\_EDIT\_SELECT\_ALL**、 **ID\_EDIT\_FIND**、 **ID\_EDIT\_REPLACE**、 **ID\_EDIT\_REPEAT**和 **ID\_FILE\_PRINT**。  
  
 `CEditView` 的默认字符限制为\(1024 \* 1024 \- 1 \= 1048575）。  这可以被调用基础的 **EM\_LIMITTEXT** 功能更改编辑控件。  但是，限制随操作系统的不同而不同，类型编辑控件\(单个或多行）。  有关这些限制的更多信息，请参见 [EM\_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607)。  
  
 若要更改在控件的此限制，请重写您的 `CEditView` 选件类和插入的 `OnCreate()` 功能以下代码行:  
  
 [!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/CPP/ceditview-class_1.cpp)]  
  
 类型 `CEditView` Objects \(从 `CEditView`派生的或的类型\)具有以下限制:  
  
-   `CEditView` 不实现true "所见即所得获得\(WYSIWYG\)编辑。  如果在可读性在屏幕和匹配的打印输出之间进行选择，`CEditView` 选择屏幕可读性。  
  
-   `CEditView` 可以显示在只只具有的文本。  特殊字符格式不支持。  为更大的函数的信息选件类 [CRichEditView](../../mfc/reference/cricheditview-class.md)。  
  
-   `CEditView` 可以包含中的文本是有限的。  限制与 `CEdit` 控件的。  
  
 有关 `CEditView`的更多信息，请参见 [派生的视图选件类可在MFC](../../mfc/derived-view-classes-available-in-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CEditView`  
  
## 要求  
 **Header:** afxext.h  
  
## 请参阅  
 [MFC示例SUPERPAD](../../top/visual-cpp-samples.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)