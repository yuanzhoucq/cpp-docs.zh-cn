---
title: "CRichEditView Class | Microsoft Docs"
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
  - "CRichEditView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditView class"
  - "document/view architecture, Rich Edit 控件"
  - "OLE containers, rich edit"
  - "Rich Edit 控件, OLE container"
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
caps.latest.revision: 25
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRichEditView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) 和 [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)，提供功能丰富在MFC的上下文中编辑文档中的控件视图结构。  
  
## 语法  
  
```  
  
class CRichEditView : public CCtrlView  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CRichEditView::CRichEditView](../Topic/CRichEditView::CRichEditView.md)|构造 `CRichEditView` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CRichEditView::AdjustDialogPosition](../Topic/CRichEditView::AdjustDialogPosition.md)|移动对话框，以便不会遮盖当前选择。|  
|[CRichEditView::CanPaste](../Topic/CRichEditView::CanPaste.md)|指示剪贴板是否包含可以粘贴到rich edit视图中的数据。|  
|[CRichEditView::DoPaste](../Topic/CRichEditView::DoPaste.md)|粘贴一个OLE项。此rich edit视图。|  
|[CRichEditView::FindText](../Topic/CRichEditView::FindText.md)|查找已指定的文本，调用等待光标。|  
|[CRichEditView::FindTextSimple](../Topic/CRichEditView::FindTextSimple.md)|查找已指定的文本。|  
|[CRichEditView::GetCharFormatSelection](../Topic/CRichEditView::GetCharFormatSelection.md)|检索当前选择的字符格式设置属性。|  
|[CRichEditView::GetDocument](../Topic/CRichEditView::GetDocument.md)|检索指向相关 [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)。|  
|[CRichEditView::GetInPlaceActiveItem](../Topic/CRichEditView::GetInPlaceActiveItem.md)|检索位于丰富的就地活动当前编辑视图的OLE项。|  
|[CRichEditView::GetMargins](../Topic/CRichEditView::GetMargins.md)|检索此的边距rich edit视图。|  
|[CRichEditView::GetPageRect](../Topic/CRichEditView::GetPageRect.md)|检索此页的矩形rich edit视图。|  
|[CRichEditView::GetPaperSize](../Topic/CRichEditView::GetPaperSize.md)|检索此的页面大小rich edit视图。|  
|[CRichEditView::GetParaFormatSelection](../Topic/CRichEditView::GetParaFormatSelection.md)|检索当前选定的段落格式设置属性。|  
|[CRichEditView::GetPrintRect](../Topic/CRichEditView::GetPrintRect.md)|检索此的打印矩形rich edit视图。|  
|[CRichEditView::GetPrintWidth](../Topic/CRichEditView::GetPrintWidth.md)|检索此的打印宽度rich edit视图。|  
|[CRichEditView::GetRichEditCtrl](../Topic/CRichEditView::GetRichEditCtrl.md)|检索rich edit控件。|  
|[CRichEditView::GetSelectedItem](../Topic/CRichEditView::GetSelectedItem.md)|从丰富检索选定项编辑视图。|  
|[CRichEditView::GetTextLength](../Topic/CRichEditView::GetTextLength.md)|检索文本的长度在丰富的编辑视图。|  
|[CRichEditView::GetTextLengthEx](../Topic/CRichEditView::GetTextLengthEx.md)|检索字符数或在丰富的字节编辑视图。  展开的标志。确定该长度方法列表。|  
|[CRichEditView::InsertFileAsObject](../Topic/CRichEditView::InsertFileAsObject.md)|插入文件作为OLE项。|  
|[CRichEditView::InsertItem](../Topic/CRichEditView::InsertItem.md)|插入新项作为OLE项。|  
|[CRichEditView::IsRichEditFormat](../Topic/CRichEditView::IsRichEditFormat.md)|指示剪贴板是否在包含数据rich edit或文本格式。|  
|[CRichEditView::OnCharEffect](../Topic/CRichEditView::OnCharEffect.md)|切换当前选择的字符格式。|  
|[CRichEditView::OnParaAlign](../Topic/CRichEditView::OnParaAlign.md)|更改段的对齐方式。|  
|[CRichEditView::OnUpdateCharEffect](../Topic/CRichEditView::OnUpdateCharEffect.md)|更新字符公共成员函数的命令用户界面。|  
|[CRichEditView::OnUpdateParaAlign](../Topic/CRichEditView::OnUpdateParaAlign.md)|更新段公共成员函数的命令用户界面。|  
|[CRichEditView::PrintInsideRect](../Topic/CRichEditView::PrintInsideRect.md)|设置在给定矩形中指定的文本。|  
|[CRichEditView::PrintPage](../Topic/CRichEditView::PrintPage.md)|设置在特定页中指定的文本。|  
|[CRichEditView::SetCharFormat](../Topic/CRichEditView::SetCharFormat.md)|将当前选择的字符格式设置属性。|  
|[CRichEditView::SetMargins](../Topic/CRichEditView::SetMargins.md)|将此的边距rich edit视图。|  
|[CRichEditView::SetPaperSize](../Topic/CRichEditView::SetPaperSize.md)|将此的页面大小rich edit视图。|  
|[CRichEditView::SetParaFormat](../Topic/CRichEditView::SetParaFormat.md)|将当前选定的段落格式设置属性。|  
|[CRichEditView::TextNotFound](../Topic/CRichEditView::TextNotFound.md)|重置该控件的内部搜索状态。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CRichEditView::GetClipboardData](../Topic/CRichEditView::GetClipboardData.md)|检索一个范围中的剪贴板对象中rich edit视图。|  
|[CRichEditView::GetContextMenu](../Topic/CRichEditView::GetContextMenu.md)|在一个正确的鼠标按钮检索上下文菜单使用下。|  
|[CRichEditView::IsSelected](../Topic/CRichEditView::IsSelected.md)|指示特定OLE项是否已选中。|  
|[CRichEditView::OnFindNext](../Topic/CRichEditView::OnFindNext.md)|查找子字符串的下一个匹配项。|  
|[CRichEditView::OnInitialUpdate](../Topic/CRichEditView::OnInitialUpdate.md)|在第一次附加到文档时，刷新视图。|  
|[CRichEditView::OnPasteNativeObject](../Topic/CRichEditView::OnPasteNativeObject.md)|从OLE项检索本机数据。|  
|[CRichEditView::OnPrinterChanged](../Topic/CRichEditView::OnPrinterChanged.md)|设置打印行为。特定设备。|  
|[CRichEditView::OnReplaceAll](../Topic/CRichEditView::OnReplaceAll.md)|用新的字符串替换特定字符串的所有匹配项。|  
|[CRichEditView::OnReplaceSel](../Topic/CRichEditView::OnReplaceSel.md)|替换当前选择。|  
|[CRichEditView::OnTextNotFound](../Topic/CRichEditView::OnTextNotFound.md)|处理用户通知未找到该请求的文本。|  
|[CRichEditView::QueryAcceptData](../Topic/CRichEditView::QueryAcceptData.md)|将查询有关 `IDataObject`的数据。|  
|[CRichEditView::WrapChanged](../Topic/CRichEditView::WrapChanged.md)|对此进行调整目标输出设备丰富基于 `m_nWordWrap`的值编辑器视图。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CRichEditView::m\_nBulletIndent](../Topic/CRichEditView::m_nBulletIndent.md)|指示量项目符号的缩进列表。|  
|[CRichEditView::m\_nWordWrap](../Topic/CRichEditView::m_nWordWrap.md)|指示自动换行约束。|  
  
## 备注  
 “rich edit控件”是用户可以输入和编辑文本的窗口。  该文本分配字符和段落格式设置，并且可以包含嵌入OLE对象。  rich edit控件为格式化文本的编程接口。  但是，应用程序必须实现必要所有用户界面的组件具有格式设置操作提供给用户。  
  
 `CRichEditView` 维护文本和格式设置典型文本。  `CRichEditDoc` 维护OLE在视图的客户端项列表。  `CRichEditCntrItem` 提供容器端对OLE客户端项目。  
  
 此Windows公共控件\(并 [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) 和相关选件类\)若要在运行Windows 95 \/98和Windows NT 3.51版下的程序可用和更高版本。  
  
 对的示例rich edit在MFC应用程序的视图，请参见 [WORDPAD](../../top/visual-cpp-samples.md) 示例应用程序。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CRichEditView`  
  
## 要求  
 **Header:** afxrich.h  
  
## 请参阅  
 [MFC示例WORDPAD](../../top/visual-cpp-samples.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc Class](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditCntrItem Class](../../mfc/reference/cricheditcntritem-class.md)