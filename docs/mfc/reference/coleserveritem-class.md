---
title: "COleServerItem Class | Microsoft Docs"
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
  - "COleServerItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleServerItem class"
  - "OLE 服务器应用程序, managing server documents"
  - "OLE 服务器应用程序, server interfaces"
  - "OLE server documents"
  - "服务器, OLE"
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleServerItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供服务器界面OLE项。  
  
## 语法  
  
```  
class COleServerItem : public CDocItem  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleServerItem::COleServerItem](../Topic/COleServerItem::COleServerItem.md)|构造 `COleServerItem` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleServerItem::AddOtherClipboardData](../Topic/COleServerItem::AddOtherClipboardData.md)|在 `COleDataSource` 对象的表示和转换格式。|  
|[COleServerItem::CopyToClipboard](../Topic/COleServerItem::CopyToClipboard.md)|复制该项目到剪贴板。|  
|[COleServerItem::DoDragDrop](../Topic/COleServerItem::DoDragDrop.md)|执行拖放操作。|  
|[COleServerItem::GetClipboardData](../Topic/COleServerItem::GetClipboardData.md)|获取数据源用于数据传输\(拖放或剪贴板）。|  
|[COleServerItem::GetDocument](../Topic/COleServerItem::GetDocument.md)|返回包含项目的服务器文档。|  
|[COleServerItem::GetEmbedSourceData](../Topic/COleServerItem::GetEmbedSourceData.md)|获取 **CF\_EMBEDSOURCE** 数据用于OLE项。|  
|[COleServerItem::GetItemName](../Topic/COleServerItem::GetItemName.md)|返回项目的名称。  用于仅链接的项。|  
|[COleServerItem::GetLinkSourceData](../Topic/COleServerItem::GetLinkSourceData.md)|获取 `CF_LINKSOURCE` 数据用于OLE项。|  
|[COleServerItem::GetObjectDescriptorData](../Topic/COleServerItem::GetObjectDescriptorData.md)|获取 **CF\_OBJECTDESCRIPTOR** 数据用于OLE项。|  
|[COleServerItem::IsConnected](../Topic/COleServerItem::IsConnected.md)|指示项目是否当前附加到一个有效的容器。|  
|[COleServerItem::IsLinkedItem](../Topic/COleServerItem::IsLinkedItem.md)|指示项目是否表示一个链接的OLE项。|  
|[COleServerItem::NotifyChanged](../Topic/COleServerItem::NotifyChanged.md)|更新具有自动连接更新的任何容器。|  
|[COleServerItem::OnDoVerb](../Topic/COleServerItem::OnDoVerb.md)|调用执行谓词。|  
|[COleServerItem::OnDraw](../Topic/COleServerItem::OnDraw.md)|调用，当容器请求绘制项目;需要的实现。|  
|[COleServerItem::OnDrawEx](../Topic/COleServerItem::OnDrawEx.md)|调用为专用的项目绘图。|  
|[COleServerItem::OnGetClipboardData](../Topic/COleServerItem::OnGetClipboardData.md)|调用由框架获取要复制到剪贴板中的数据。|  
|[COleServerItem::OnGetExtent](../Topic/COleServerItem::OnGetExtent.md)|调用由框架检索OLE项的大小。|  
|[COleServerItem::OnInitFromData](../Topic/COleServerItem::OnInitFromData.md)|调用framework初始化OLE项使用指定的数据传输对象的内容。|  
|[COleServerItem::OnQueryUpdateItems](../Topic/COleServerItem::OnQueryUpdateItems.md)|调用确定任何链接的项目是否需要更新。|  
|[COleServerItem::OnRenderData](../Topic/COleServerItem::OnRenderData.md)|为延迟呈现的一部分，检索数据。|  
|[COleServerItem::OnRenderFileData](../Topic/COleServerItem::OnRenderFileData.md)|为延迟呈现的一部分，检索数据。`CFile` 对象。|  
|[COleServerItem::OnRenderGlobalData](../Topic/COleServerItem::OnRenderGlobalData.md)|为延迟呈现的一部分，检索数据。`HGLOBAL`。|  
|[COleServerItem::OnSetColorScheme](../Topic/COleServerItem::OnSetColorScheme.md)|调用设置项目的配色方案。|  
|[COleServerItem::OnSetData](../Topic/COleServerItem::OnSetData.md)|调用设置项目的数据。|  
|[COleServerItem::OnSetExtent](../Topic/COleServerItem::OnSetExtent.md)|调用由框架设置OLE项的大小。|  
|[COleServerItem::OnUpdate](../Topic/COleServerItem::OnUpdate.md)|调用，当文档的某些部分该项所属时更改。|  
|[COleServerItem::OnUpdateItems](../Topic/COleServerItem::OnUpdateItems.md)|调用更新表示缓存在服务器上的所有项目文档。|  
|[COleServerItem::SetItemName](../Topic/COleServerItem::SetItemName.md)|设置项目的名称。  用于仅链接的项。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[COleServerItem::GetDataSource](../Topic/COleServerItem::GetDataSource.md)|获取对象用于存储转换格式。|  
|[COleServerItem::OnHide](../Topic/COleServerItem::OnHide.md)|调用由框架隐藏OLE项。|  
|[COleServerItem::OnOpen](../Topic/COleServerItem::OnOpen.md)|调用框架在自己的顶级窗口的OLE项。|  
|[COleServerItem::OnShow](../Topic/COleServerItem::OnShow.md)|调用，当容器请求显示项目。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COleServerItem::m\_sizeExtent](../Topic/COleServerItem::m_sizeExtent.md)|通知数的服务器OLE项可见。|  
  
## 备注  
 链接项可以表示某些或所有服务器文档。  一个嵌入项始终表示整个服务器文档。  
  
 `COleServerItem` 选件类通常定义由OLE系统动态链接库\(DLLs\)调用的若干可重写的成员函数，以响应从容器应用程序的请求。  这些成员函数允许容器应用程序取消操作项以多种方式，例如通过显示它，执行其谓词以检索其数据以多种格式。  
  
 若要使用 `COleServerItem`，从中派生选件类并实现 [OnDraw](../Topic/COleServerItem::OnDraw.md) 和 [序列化](../Topic/CObject::Serialize.md) 成员函数。  当容器应用程序打开多个文档时，`OnDraw` 功能提供项目的图元文件表示，允许它显示。  `CObject` 的 `Serialize` 功能提供项目的本机表示，允许一个嵌入项调用在服务器和容器应用程序之间。  [OnGetExtent](../Topic/COleServerItem::OnGetExtent.md) 提供项的原始大小到容器，使容器调整该项目。  
  
 有关服务器和相关主题的更多信息，请参见文章 [服务器:实现服务器](../../mfc/servers-implementing-a-server.md) 和“创建容器\/服务器应用”。这篇文章 [容器:高级功能](../../mfc/containers-advanced-features.md)上。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleServerItem`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [MFC示例HIERSVR](../../top/visual-cpp-samples.md)   
 [CDocItem Class](../../mfc/reference/cdocitem-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [COleServerDoc Class](../../mfc/reference/coleserverdoc-class.md)   
 [COleTemplateServer Class](../../mfc/reference/coletemplateserver-class.md)