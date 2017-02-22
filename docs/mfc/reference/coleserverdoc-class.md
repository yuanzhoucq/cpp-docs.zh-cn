---
title: "COleServerDoc Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleServerDoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleServerDoc class"
  - "container/server applications"
  - "OLE containers, server documents"
  - "OLE 服务器应用程序, managing server documents"
  - "OLE server documents"
  - "server documents, OLE"
  - "服务器, OLE"
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# COleServerDoc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE服务器的基类文档。  
  
## 语法  
  
```  
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleServerDoc::COleServerDoc](../Topic/COleServerDoc::COleServerDoc.md)|构造 `COleServerDoc` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleServerDoc::ActivateDocObject](../Topic/COleServerDoc::ActivateDocObject.md)|激活关联的DocObject文档。|  
|[COleServerDoc::ActivateInPlace](../Topic/COleServerDoc::ActivateInPlace.md)|激活就地编辑的文档。|  
|[COleServerDoc::DeactivateAndUndo](../Topic/COleServerDoc::DeactivateAndUndo.md)|停用服务器的用户界面。|  
|[COleServerDoc::DiscardUndoState](../Topic/COleServerDoc::DiscardUndoState.md)|放弃取消状态信息。|  
|[COleServerDoc::GetClientSite](../Topic/COleServerDoc::GetClientSite.md)|检索指向基础 `IOleClientSite` 接口。|  
|[COleServerDoc::GetEmbeddedItem](../Topic/COleServerDoc::GetEmbeddedItem.md)|返回指向表示整个项目的文档。|  
|[COleServerDoc::GetItemClipRect](../Topic/COleServerDoc::GetItemClipRect.md)|返回就地编辑的当前剪辑矩形。|  
|[COleServerDoc::GetItemPosition](../Topic/COleServerDoc::GetItemPosition.md)|返回当前位置矩形，相对于容器应用程序的工作区，就地编辑的。|  
|[COleServerDoc::GetZoomFactor](../Topic/COleServerDoc::GetZoomFactor.md)|返回在像素的缩放比例。|  
|[COleServerDoc::IsDocObject](../Topic/COleServerDoc::IsDocObject.md)|确定文档是否是DocObject。|  
|[COleServerDoc::IsEmbedded](../Topic/COleServerDoc::IsEmbedded.md)|指示文档是否在容器中嵌入文档或独立运行。|  
|[COleServerDoc::IsInPlaceActive](../Topic/COleServerDoc::IsInPlaceActive.md)|如果例如，当前激活该项目返回 `TRUE`。|  
|[COleServerDoc::NotifyChanged](../Topic/COleServerDoc::NotifyChanged.md)|通知容器用户更改了文档。|  
|[COleServerDoc::NotifyClosed](../Topic/COleServerDoc::NotifyClosed.md)|通知容器用户关闭文档。|  
|[COleServerDoc::NotifyRename](../Topic/COleServerDoc::NotifyRename.md)|通知容器用户将文档重命名。|  
|[COleServerDoc::NotifySaved](../Topic/COleServerDoc::NotifySaved.md)|通知容器用户保存的文档。|  
|[COleServerDoc::OnDeactivate](../Topic/COleServerDoc::OnDeactivate.md)|调用由结构，当用户停用就地激活的项目。|  
|[COleServerDoc::OnDeactivateUI](../Topic/COleServerDoc::OnDeactivateUI.md)|调用由框架销毁为就地激活和其他用户界面元素创建的控件。|  
|[COleServerDoc::OnDocWindowActivate](../Topic/COleServerDoc::OnDocWindowActivate.md)|调用由框架，在容器的文档时激活框架窗口或停用。|  
|[COleServerDoc::OnResizeBorder](../Topic/COleServerDoc::OnResizeBorder.md)|调用由框架，当容器应用程序的框架窗口或文档窗口调整大小。|  
|[COleServerDoc::OnShowControlBars](../Topic/COleServerDoc::OnShowControlBars.md)|调用由结构显示或隐藏就地编辑的控制条。|  
|[COleServerDoc::OnUpdateDocument](../Topic/COleServerDoc::OnUpdateDocument.md)|调用由框架是，在嵌入式项目的服务器文档时保存，更新项目的容器的副本。|  
|[COleServerDoc::RequestPositionChange](../Topic/COleServerDoc::RequestPositionChange.md)|更改就地编辑框架的位置。|  
|[COleServerDoc::SaveEmbedding](../Topic/COleServerDoc::SaveEmbedding.md)|调用容器应用保存文档。|  
|[COleServerDoc::ScrollContainerBy](../Topic/COleServerDoc::ScrollContainerBy.md)|移动容器文档。|  
|[COleServerDoc::UpdateAllItems](../Topic/COleServerDoc::UpdateAllItems.md)|通知容器用户更改了文档。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[COleServerDoc::CreateInPlaceFrame](../Topic/COleServerDoc::CreateInPlaceFrame.md)|调用由框架创建就地编辑的框架窗口。|  
|[COleServerDoc::DestroyInPlaceFrame](../Topic/COleServerDoc::DestroyInPlaceFrame.md)|调用由框架销毁就地编辑的框架窗口。|  
|[COleServerDoc::GetDocObjectServer](../Topic/COleServerDoc::GetDocObjectServer.md)|重写此功能创建新 `CDocObjectServer` 对象，并指示文档是DocObject容器。|  
|[COleServerDoc::OnClose](../Topic/COleServerDoc::OnClose.md)|调用由结构，当容器请求关闭文档。|  
|[COleServerDoc::OnExecOleCmd](../Topic/COleServerDoc::OnExecOleCmd.md)|执行一个指定的命令或显示为命令帮助。|  
|[COleServerDoc::OnFrameWindowActivate](../Topic/COleServerDoc::OnFrameWindowActivate.md)|调用由框架激活时，容器的框架窗口或停用。|  
|[COleServerDoc::OnGetEmbeddedItem](../Topic/COleServerDoc::OnGetEmbeddedItem.md)|页中获取 `COleServerItem` 表示的整个文档;用于获取一个嵌入项。  需要的实现。|  
|[COleServerDoc::OnReactivateAndUndo](../Topic/COleServerDoc::OnReactivateAndUndo.md)|调用由框架在取消就地编辑过程中所做的更改。|  
|[COleServerDoc::OnSetHostNames](../Topic/COleServerDoc::OnSetHostNames.md)|调用由结构，当容器设置一个嵌入对象的窗口标题。|  
|[COleServerDoc::OnSetItemRects](../Topic/COleServerDoc::OnSetItemRects.md)|调用由框架确定在容器应用程序的窗口中就地编辑框架窗口。|  
|[COleServerDoc::OnShowDocument](../Topic/COleServerDoc::OnShowDocument.md)|调用由结构显示或隐藏文档。|  
  
## 备注  
 服务器文档可以包含 [COleServerItem](../../mfc/reference/coleserveritem-class.md) 对象，该对象表示服务器接口嵌入或链接的项。  当服务器应用程序由容器生成编辑嵌入式项目时，项目将加载，其自己的服务器文档; `COleServerDoc` 对象包含一 `COleServerItem` 对象，包括整个文档。  当服务器应用程序由容器生成编辑链接项时，现有文档从磁盘加载;文档内容的部分显示一个链接的项。  
  
 `COleServerDoc` 对象也可以包含 [COleClientItem](../../mfc/reference/coleclientitem-class.md) 选件类的项目。  这允许您创建容器服务器应用程序。  该结构提供了适当地存储 `COleClientItem` 项，则为 `COleServerItem` 对象服务时。  
  
 如果您的服务器应用程序不支持连接，服务器文档只将始终包含一个服务器项目，表示整个嵌入对象作为文档。  如果您的服务器应用程序支持连接时，它必须创建服务器项目，每次选择复制到剪贴板。  
  
 若要使用 `COleServerDoc`，从中派生选件类并实现 [OnGetEmbeddedItem](../Topic/COleServerDoc::OnGetEmbeddedItem.md) 成员函数，允许您的服务器支持嵌入项。  从 `COleServerItem` 派生选件类实现在项目中文档，并返回该选件类对象从 `OnGetEmbeddedItem`的。  
  
 若要支持链接的项目，`COleServerDoc` 提供 [OnGetLinkedItem](../Topic/COleLinkingDoc::OnGetLinkedItem.md) 成员函数。  如果您的方式尝试文档项目，可以使用默认实现或重写它。  
  
 您需要一 `COleServerDoc`\-服务器的每种类型的派生类编写应用程序。  例如，因此，如果您的服务器应用程序支持工作表和图表，需要两 `COleServerDoc`派生类。  
  
 有关服务器的更多信息，请参见文章 [服务器:实现服务器](../../mfc/servers-implementing-a-server.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 `COleServerDoc`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [MFC示例HIERSVR](../../top/visual-cpp-samples.md)   
 [COleLinkingDoc Class](../../mfc/reference/colelinkingdoc-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDocument Class](../../mfc/reference/coledocument-class.md)   
 [COleLinkingDoc Class](../../mfc/reference/colelinkingdoc-class.md)   
 [COleTemplateServer Class](../../mfc/reference/coletemplateserver-class.md)