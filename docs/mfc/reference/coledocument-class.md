---
title: "COleDocument Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDocument"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDocument class"
  - "文档, OLE"
  - "OLE containers, client items"
  - "OLE 文档"
  - "OLE 文档, 基类"
  - "visual editing, OLE document base class"
ms.assetid: dc2ecb99-03e1-44c7-bb69-48056dd1b672
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# COleDocument Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE的基类文档支持可视编辑。  
  
## 语法  
  
```  
class COleDocument : public CDocument  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleDocument::COleDocument](../Topic/COleDocument::COleDocument.md)|构造 `COleDocument` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleDocument::AddItem](../Topic/COleDocument::AddItem.md)|向文档维护的项列表。|  
|[COleDocument::ApplyPrintDevice](../Topic/COleDocument::ApplyPrintDevice.md)|将所有客户端项目的输出目标设备在文档。|  
|[COleDocument::EnableCompoundFile](../Topic/COleDocument::EnableCompoundFile.md)|使用OLE结构化存储文件格式，原因文档存储。|  
|[COleDocument::GetInPlaceActiveItem](../Topic/COleDocument::GetInPlaceActiveItem.md)|返回当前处于就地活动状态的OLE项。|  
|[COleDocument::GetNextClientItem](../Topic/COleDocument::GetNextClientItem.md)|获取重复的下一个客户端项目。|  
|[COleDocument::GetNextItem](../Topic/COleDocument::GetNextItem.md)|获取下文档重复项。|  
|[COleDocument::GetNextServerItem](../Topic/COleDocument::GetNextServerItem.md)|获取重复的下一个服务器项目。|  
|[COleDocument::GetPrimarySelectedItem](../Topic/COleDocument::GetPrimarySelectedItem.md)|返回在文档的主要选定的OLE项。|  
|[COleDocument::GetStartPosition](../Topic/COleDocument::GetStartPosition.md)|获取初始位置开始迭代。|  
|[COleDocument::HasBlankItems](../Topic/COleDocument::HasBlankItems.md)|空白项目的检查文档中。|  
|[COleDocument::OnShowViews](../Topic/COleDocument::OnShowViews.md)|调用，则此变为可见或不可见。|  
|[COleDocument::RemoveItem](../Topic/COleDocument::RemoveItem.md)|从文档中维护的项列表移除项。|  
|[COleDocument::UpdateModifiedFlag](../Topic/COleDocument::UpdateModifiedFlag.md)|如果修改了，将该文档标记为已修改任何一个包含的OLE项。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[COleDocument::OnEditChangeIcon](../Topic/COleDocument::OnEditChangeIcon.md)|在更改图标菜单命令的事件。|  
|[COleDocument::OnEditConvert](../Topic/COleDocument::OnEditConvert.md)|处理一个嵌入或链接的对象从一种类型转换为另一个。|  
|[COleDocument::OnEditLinks](../Topic/COleDocument::OnEditLinks.md)|在链接的事件在"编辑"菜单命令。|  
|[COleDocument::OnFileSendMail](../Topic/COleDocument::OnFileSendMail.md)|发送与附加文档的消息信息。|  
|[COleDocument::OnUpdateEditChangeIcon](../Topic/COleDocument::OnUpdateEditChangeIcon.md)|调用由框架更新编辑\/更改图标菜单选项的命令用户界面。|  
|[COleDocument::OnUpdateEditLinksMenu](../Topic/COleDocument::OnUpdateEditLinksMenu.md)|调用由框架更新编辑\/链接菜单上的命令用户界面选项。|  
|[COleDocument::OnUpdateObjectVerbMenu](../Topic/COleDocument::OnUpdateObjectVerbMenu.md)|调用由框架更新编辑\/*ObjectName* 菜单上的命令用户界面选项和谓词子菜单访问已从编辑\/*ObjectName*。|  
|[COleDocument::OnUpdatePasteLinkMenu](../Topic/COleDocument::OnUpdatePasteLinkMenu.md)|调用由框架更新粘贴特定菜单选项的命令用户界面。|  
|[COleDocument::OnUpdatePasteMenu](../Topic/COleDocument::OnUpdatePasteMenu.md)|调用由框架更新粘贴菜单选项的命令用户界面。|  
  
## 备注  
 `COleDocument` 从 **CDocument**派生，允许您的OLE应用程序使用Microsoft基础选件类库提供的文档\/视图结构。  
  
 `COleDocument` 将文档作为 [CDocItem](../../mfc/reference/cdocitem-class.md) 对象的集合传递给处理OLE项的。  因为它们文档必须能够包含OLE项，容器和服务器应用程序需要这一结构。  [COleServerItem](../../mfc/reference/coleserveritem-class.md) 和 [COleClientItem](../../mfc/reference/coleclientitem-class.md) 选件类，从 `CDocItem`派生的两个，管理应用程序和OLE项之间的交互。  
  
 如果正在编写一个简单的容器应用程序，请从\+中派生您从文档 `COleDocument`的选件类。  如果您编写支持链接到它所包含的嵌入项的容器应用程序文档，派生自己文档从 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)的选件类。  如果正在编写一个服务器应用程序或组合容器\/服务器，请从\+中派生您从文档 [COleServerDoc](../../mfc/reference/coleserverdoc-class.md)的选件类。  `COleLinkingDoc` 和 `COleServerDoc` 从 `COleDocument`派生，因此，这些选件类继承的所有服务可供在 `COleDocument` 和 **CDocument**。  
  
 若要使用 `COleDocument`，从中派生选件类并添加功能管理应用程序的非OLE数据以及嵌入或链接的项。  如果定义 `CDocItem`\-存储应用程序的本机数据的派生类，可以使用 `COleDocument` 定义的默认实现存储您的OLE和非OLE数据。  还可以设计您单独存储的非OLE数据自己的数据结构与OLE项。  有关更多信息，请参见文章 [容器:复合文件](../../mfc/containers-compound-files.md)。  
  
 **CDocument** 支持向您发送消息传递文档，如果消息支持\(mapi\)存在。  `COleDocument` 正确更新了 [OnFileSendMail](../Topic/COleDocument::OnFileSendMail.md) 处理多个文档。  有关更多信息，请参见位于 [MAPI](../../mfc/mapi.md) 和 [MAPI在MFC支持](../../mfc/mapi-support-in-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `COleDocument`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [MFC砂样瓶](../../top/visual-cpp-samples.md)   
 [MFC示例MFCBIND](../../top/visual-cpp-samples.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)