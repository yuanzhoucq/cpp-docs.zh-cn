---
title: "CDocTemplate Class | Microsoft Docs"
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
  - "CDocTemplate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDocTemplate class"
  - "文档模板"
  - "模板, 文档"
ms.assetid: 14b41a1f-bf9d-4eac-b6a8-4c54ffcc77f6
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDocTemplate Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定义基本功能的抽象基类文档模板。  
  
## 语法  
  
```  
class CDocTemplate : public CCmdTarget  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDocTemplate::CDocTemplate](../Topic/CDocTemplate::CDocTemplate.md)|构造 `CDocTemplate` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDocTemplate::AddDocument](../Topic/CDocTemplate::AddDocument.md)|添加文档到模板。|  
|[CDocTemplate::CloseAllDocuments](../Topic/CDocTemplate::CloseAllDocuments.md)|关闭所有文档与该模板。|  
|[CDocTemplate::CreateNewDocument](../Topic/CDocTemplate::CreateNewDocument.md)|创建新文档。|  
|[CDocTemplate::CreateNewFrame](../Topic/CDocTemplate::CreateNewFrame.md)|创建包含文档和视图的新框架窗口。|  
|[CDocTemplate::CreateOleFrame](../Topic/CDocTemplate::CreateOleFrame.md)|创建OLE启用框架窗口。|  
|[CDocTemplate::CreatePreviewFrame](../Topic/CDocTemplate::CreatePreviewFrame.md)|创建用于丰富预览的子帧。|  
|[CDocTemplate::GetDocString](../Topic/CDocTemplate::GetDocString.md)|检索字符串关联的文件类型。|  
|[CDocTemplate::GetFirstDocPosition](../Topic/CDocTemplate::GetFirstDocPosition.md)|检索位置第一个文档与该模板。|  
|[CDocTemplate::GetNextDoc](../Topic/CDocTemplate::GetNextDoc.md)|检索文档和位置下一个。|  
|[CDocTemplate::InitialUpdateFrame](../Topic/CDocTemplate::InitialUpdateFrame.md)|初始化框架窗口和\(可选\)以使其可见。|  
|[CDocTemplate::LoadTemplate](../Topic/CDocTemplate::LoadTemplate.md)|加载特定 `CDocTemplate` 或派生类的资源。|  
|[CDocTemplate::MatchDocType](../Topic/CDocTemplate::MatchDocType.md)|确定信心要匹配的"文件类型和此模板之间。|  
|[CDocTemplate::OpenDocumentFile](../Topic/CDocTemplate::OpenDocumentFile.md)|打开路径名指定的文件。|  
|[CDocTemplate::RemoveDocument](../Topic/CDocTemplate::RemoveDocument.md)|从模板取消文档。|  
|[CDocTemplate::SaveAllModified](../Topic/CDocTemplate::SaveAllModified.md)|保存修改的所有文档与该模板。|  
|[CDocTemplate::SetContainerInfo](../Topic/CDocTemplate::SetContainerInfo.md)|编辑一个就地OLE项时，确保OLE容器的资源中。|  
|[CDocTemplate::SetDefaultTitle](../Topic/CDocTemplate::SetDefaultTitle.md)|在文档窗口的标题栏显示默认的前缀。|  
|[CDocTemplate::SetPreviewInfo](../Topic/CDocTemplate::SetPreviewInfo.md)|设置在外部处理预览处理程序。|  
|[CDocTemplate::SetServerInfo](../Topic/CDocTemplate::SetServerInfo.md)|确定资源，所以，当服务器文档时嵌入选件类或编辑的就地。|  
  
## 备注  
 通常创建一个或多个文档在应用程序中 `InitInstance` 功能的实现模板。  文档模板定义了选件类中的三种类型的关系:  
  
-   文档选件类，则从 **CDocument**派生。  
  
-   视图选件类，显示从文档选件类的数据上面列出的。  可以从 `CView`、 `CScrollView`、 `CFormView`或 `CEditView`派生此选件类。  （可以直接还使用 `CEditView`。）  
  
-   框架窗口选件类，包含视图。  对于单文档界面\(SDI\)应用程序，则从派生 `CFrameWnd`此选件类。  对于多文档界面\(mdi\) \(MDI\)应用程序，则从派生 `CMDIChildWnd`此选件类。  如果不需要自定义框架窗口的行为，则可以使用 `CFrameWnd` 或 `CMDIChildWnd` 直接，而无需派生您的选件类。  
  
 您的应用程序有一个记录每个类型的模板文档它支持。  例如，因此，如果您的应用程序支持电子表格，并文本文档，应用程序具有两个文档模板对象。  每个文档模板用于创建负责，并管理所有文档其类型。  
  
 文档模板存储指向文档、视图和框架窗口选件类的 `CRuntimeClass` 对象。  当构造文档模板时，这些 `CRuntimeClass` 对象指定。  
  
 文档模板包含资源的ID用于文件类型\(如菜单、图标或快捷键对应表资源）。  文档模板还包含有关其的字符串附加信息文件类型。  其中包括文件类型\(例如，“工作表”\)和文件扩展名\(例如，“.xls”\)的名称。  或者，它可以包含应用程序的用户界面使用的其他字符串，Windows文件管理器，因此，对象链接和嵌入技术\(OLE\)的支持。  
  
 如果应用程序是OLE容器和服务器，文档模板还定义了就地激活时使用菜单的ID。  如果应用程序是OLE服务器，文档模板定义了就地激活时和菜单的ID工具栏。  通过调用 `SetContainerInfo` 和 `SetServerInfo`指定这些附加OLE资源。  
  
 由于 `CDocTemplate` 是一个抽象类，您不能直接使用选件类。  典型的应用程序使用一 `CDocTemplate`\- Microsoft基础选件类库提供的派生类: `CSingleDocTemplate`，实现SDI和 `CMultiDocTemplate`，实现MDI。  这些参见选件类有关文档的更多信息模板的使用。  
  
 如果应用程序需要在功能上不同于SDI或MDI的用户界面示例，您可以从 `CDocTemplate`派生您的选件类。  
  
 有关 `CDocTemplate`的更多信息，请参见 [文档模板，而且文档\/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocTemplate`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CSingleDocTemplate Class](../../mfc/reference/csingledoctemplate-class.md)   
 [CMultiDocTemplate Class](../../mfc/reference/cmultidoctemplate-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CScrollView Class](../../mfc/reference/cscrollview-class.md)   
 [CEditView Class](../../mfc/reference/ceditview-class.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md)