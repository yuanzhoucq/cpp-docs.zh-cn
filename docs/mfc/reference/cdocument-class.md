---
title: "CDocument Class | Microsoft Docs"
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
  - "CDocument"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDocument class"
  - "命令处理, documents and"
  - "命令传送, documents and"
  - "文档 [C++], 命令传送"
  - "文档 [C++], document classes"
  - "文档 [C++], 多个视图"
  - "文档 [C++], 序列化"
  - "文件 [C++], 文档"
  - "序列化 [C++], documents and"
  - "视图 [C++], 文档"
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
caps.latest.revision: 21
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDocument Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为用户定义提供了基本功能文档选件类。  
  
## 语法  
  
```  
class CDocument : public CCmdTarget  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDocument::CDocument](../Topic/CDocument::CDocument.md)|构造 `CDocument` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDocument::AddView](../Topic/CDocument::AddView.md)|附加视图到文档中。|  
|[CDocument::BeginReadChunks](../Topic/CDocument::BeginReadChunks.md)|初始化区块阅读。|  
|[CDocument::CanCloseFrame](../Topic/CDocument::CanCloseFrame.md)|高级可重写;调用关闭查看此框架窗口之前文档。|  
|[CDocument::ClearChunkList](../Topic/CDocument::ClearChunkList.md)|清除区块列表。|  
|[CDocument::ClearPathName](../Topic/CDocument::ClearPathName.md)|扫清路径文档对象。|  
|[CDocument::DeleteContents](../Topic/CDocument::DeleteContents.md)|调用执行文档的清理。|  
|[CDocument::FindChunk](../Topic/CDocument::FindChunk.md)|查找具有指定的GUID的区块。|  
|[CDocument::GetAdapter](../Topic/CDocument::GetAdapter.md)|返回指向 `IDocument` 实现接口的对象。|  
|[CDocument::GetDocTemplate](../Topic/CDocument::GetDocTemplate.md)|返回指向描述文档类型的文档模板。|  
|[CDocument::GetFile](../Topic/CDocument::GetFile.md)|返回指向所需 `CFile` 对象。|  
|[CDocument::GetFirstViewPosition](../Topic/CDocument::GetFirstViewPosition.md)|返回位置的第一个视图列表;用于开始迭代。|  
|[CDocument::GetNextView](../Topic/CDocument::GetNextView.md)|通过视图中列出的重复与文档。|  
|[CDocument::GetPathName](../Topic/CDocument::GetPathName.md)|返回文档的数据文件的路径。|  
|[CDocument::GetThumbnail](../Topic/CDocument::GetThumbnail.md)|调用创建缩略图提供程序将使用的位图显示缩略图。|  
|[CDocument::GetTitle](../Topic/CDocument::GetTitle.md)|返回文档的标题。|  
|[CDocument::InitializeSearchContent](../Topic/CDocument::InitializeSearchContent.md)|调用初始化搜索处理程序的搜索目录。|  
|[CDocument::IsModified](../Topic/CDocument::IsModified.md)|指示是否已修改文档，则它上次保存了。|  
|[CDocument::IsSearchAndOrganizeHandler](../Topic/CDocument::IsSearchAndOrganizeHandler.md)|指示 `CDocument` 对象此实例是否为搜索已创建&组织处理程序。|  
|[CDocument::LoadDocumentFromStream](../Topic/CDocument::LoadDocumentFromStream.md)|对加载文档从流的数据。|  
|[CDocument::OnBeforeRichPreviewFontChanged](../Topic/CDocument::OnBeforeRichPreviewFontChanged.md)|对丰富预览字体时更改。|  
|[CDocument::OnChangedViewList](../Topic/CDocument::OnChangedViewList.md)|调用，在视图中添加或从文档后移除。|  
|[CDocument::OnCloseDocument](../Topic/CDocument::OnCloseDocument.md)|调用关闭文档。|  
|[CDocument::OnCreatePreviewFrame](../Topic/CDocument::OnCreatePreviewFrame.md)|调用由框架，则需要创建丰富预览的预览帧。|  
|[CDocument::OnDocumentEvent](../Topic/CDocument::OnDocumentEvent.md)|调用由结构以响应文档事件。|  
|[CDocument::OnDrawThumbnail](../Topic/CDocument::OnDrawThumbnail.md)|具有派生类中重写此方法绘制缩略图内容。|  
|[CDocument::OnLoadDocumentFromStream](../Topic/CDocument::OnLoadDocumentFromStream.md)|调用由框架，则需要从流加载文档数据。|  
|[CDocument::OnNewDocument](../Topic/CDocument::OnNewDocument.md)|调用创建新文档。|  
|[CDocument::OnOpenDocument](../Topic/CDocument::OnOpenDocument.md)|调用打开现有文档。|  
|[CDocument::OnPreviewHandlerQueryFocus](../Topic/CDocument::OnPreviewHandlerQueryFocus.md)|处理预览处理程序调用返回GetFocus功能的HWND。|  
|[CDocument::OnPreviewHandlerTranslateAccelerator](../Topic/CDocument::OnPreviewHandlerTranslateAccelerator.md)|处理预览处理程序添加到击键从处理消息泵通过预览运行处理程序的处理。|  
|[CDocument::OnRichPreviewBackColorChanged](../Topic/CDocument::OnRichPreviewBackColorChanged.md)|调用，当丰富预览背景色更改为。|  
|[CDocument::OnRichPreviewFontChanged](../Topic/CDocument::OnRichPreviewFontChanged.md)|调用，当丰富预览字体已更改。|  
|[CDocument::OnRichPreviewSiteChanged](../Topic/CDocument::OnRichPreviewSiteChanged.md)|调用，当丰富预览站点已更改。|  
|[CDocument::OnRichPreviewTextColorChanged](../Topic/CDocument::OnRichPreviewTextColorChanged.md)|调用，当丰富预览文本颜色更改为。|  
|[CDocument::OnSaveDocument](../Topic/CDocument::OnSaveDocument.md)|调用将文档保存到磁盘。|  
|[CDocument::OnUnloadHandler](../Topic/CDocument::OnUnloadHandler.md)|调用由结构，当预览处理程序卸载。|  
|[CDocument::PreCloseFrame](../Topic/CDocument::PreCloseFrame.md)|在框架窗口之前调用关闭。|  
|[CDocument::ReadNextChunkValue](../Topic/CDocument::ReadNextChunkValue.md)|读取下一个区块值。|  
|[CDocument::ReleaseFile](../Topic/CDocument::ReleaseFile.md)|显示文件使其可供其他应用程序。|  
|[CDocument::RemoveChunk](../Topic/CDocument::RemoveChunk.md)|移除区块使用指定的GUID。|  
|[CDocument::RemoveView](../Topic/CDocument::RemoveView.md)|分离文档的视图。|  
|[CDocument::ReportSaveLoadException](../Topic/CDocument::ReportSaveLoadException.md)|高级可重写;调用因为异常，那么，当打开或保存操作无法完成。|  
|[CDocument::SaveModified](../Topic/CDocument::SaveModified.md)|高级可重写;调用来询问用户是否应保存文档。|  
|[CDocument::SetChunkValue](../Topic/CDocument::SetChunkValue.md)|设置区块值。|  
|[CDocument::SetModifiedFlag](../Topic/CDocument::SetModifiedFlag.md)|设置指示的标志您修改了文档，则它上次保存了。|  
|[CDocument::SetPathName](../Topic/CDocument::SetPathName.md)|设置文档使用的数据文件的路径。|  
|[CDocument::SetTitle](../Topic/CDocument::SetTitle.md)|设置文档的标题。|  
|[CDocument::UpdateAllViews](../Topic/CDocument::UpdateAllViews.md)|通知文档修改的所有视图。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CDocument::OnFileSendMail](../Topic/CDocument::OnFileSendMail.md)|发送与附加文档的消息信息。|  
|[CDocument::OnUpdateFileSendMail](../Topic/CDocument::OnUpdateFileSendMail.md)|如果消息支持存在，启用消息发送命令。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDocument::m\_bGetThumbnailMode](../Topic/CDocument::m_bGetThumbnailMode.md)|指定 `CDocument` 对象由缩略图的dllhost创建。  应签入 `CView::OnDraw`。|  
|[CDocument::m\_bPreviewHandlerMode](../Topic/CDocument::m_bPreviewHandlerMode.md)|指定 `CDocument` 对象由 `Rich Preview`的prevhost创建。  应签入 `CView::OnDraw`。|  
|[CDocument::m\_bSearchMode](../Topic/CDocument::m_bSearchMode.md)|指定 `CDocument` 对象由索引器或其他创建的搜索应用程序。|  
|[CDocument::m\_clrRichPreviewBackColor](../Topic/CDocument::m_clrRichPreviewBackColor.md)|指定丰富预览窗口的背景色。  此色由主机设置。|  
|[CDocument::m\_clrRichPreviewTextColor](../Topic/CDocument::m_clrRichPreviewTextColor.md)|指定丰富预览窗口中的前景色。  此色由主机设置。|  
|[CDocument::m\_lfRichPreviewFont](../Topic/CDocument::m_lfRichPreviewFont.md)|为丰富预览窗口指定文本的字体。  此字体信息由宿主设置。|  
  
## 备注  
 文档表示用户通常打开与该文件打开命令并保存该文件保存订单数据的单元。  
  
 **CDocument** 支持标准操作\(例如创建文档，加载它并保存它。  框架操作文档使用 **CDocument**定义的接口。  
  
 应用程序可以支持多个文档类型;例如，应用程序可能支持电子表格，并文本文档。  每个文档类型具有关联文档模板;文档模板指定哪些资源\(例如，菜单、图标或快捷键对应表\)为该类型使用文档。  每个文档包含指向其关联的 `CDocTemplate` 对象。  
  
 用户与文档进行交互。[CView](../../mfc/reference/cview-class.md) 对象与之关联的。  视图呈现文档的图像在框架窗口并解释为文档的操作中的用户输入。  文档可以包含多个关联的视图。  当用户打开在文档窗口时，结构创建视图并将其附加到文档中。  文档模板指定类型的视图和框架窗口用于显示每种类型的文档。  
  
 文档是结构的标准命令传送的一部分而接收来自标准用户界面元素的命令\(例如文件保存菜单项）。  文档接收事件视图转发的命令。  如果文档不处理特定的命令，则到管理它的文档模板中的指令。  
  
 当修改时文件中的数据，其视图中的每个必须反映这些更改。  **CDocument** 提供了 [UpdateAllViews](../Topic/CDocument::UpdateAllViews.md) 成员函数通知视图这样的更改，因此，视图可以根据需要重新绘制自身。  该结构还会提示用户在关闭前保存已修改的文件。  
  
 若要实现在典型的应用程序，则文档必须执行以下操作:  
  
-   从每种类型的 **CDocument** 派生选件类文档。  
  
-   添加成员变量存储每个文件中的数据。  
  
-   实现读取和修改文档的数据成员函数。  文档的视图是这些成员函数的最重要的用户。  
  
-   重写在您的功能文档选件类编写以及向\/从磁盘读取文档中的数据的 [CObject::Serialize](../Topic/CObject::Serialize.md) 成员。  
  
 **CDocument** 支持向您发送消息传递文档，如果消息支持\(mapi\)存在。  请参见文章 [MAPI](../../mfc/mapi.md) 和 [MAPI在MFC支持](../../mfc/mapi-support-in-mfc.md)。  
  
 有关 **CDocument**的更多信息，请参见 [序列化](../../mfc/serialization-in-mfc.md)、 [文档\/视图结构主题](../../mfc/document-view-architecture.md)和 [文档\/视图创建](../../mfc/document-view-creation.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocument`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC MDIDOCVW示例](../../top/visual-cpp-samples.md)   
 [MFC SNAPVW示例](../../top/visual-cpp-samples.md)   
 [MFC NPP示例](../../top/visual-cpp-samples.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)