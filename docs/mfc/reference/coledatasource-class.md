---
title: "COleDataSource Class | Microsoft Docs"
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
  - "COleDataSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "剪贴板 [C++], MFC 支持"
  - "剪贴板 [C++], OLE 支持"
  - "COleDataSource class"
  - "data transfer [C++], OLE"
  - "drag and drop [C++], MFC 支持"
  - "IDataObject, MFC encapsulation"
  - "OLE [C++], uniform data transfer"
  - "OLE Clipboard [C++], 支持"
  - "OLE data transfer [C++]"
  - "uniform data transfer"
  - "uniform data transfer, OLE"
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDataSource Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为应用程序将数据将提供的缓存在数据传输操作期间，例如剪贴板或拖放操作。  
  
## 语法  
  
```  
class COleDataSource : public CCmdTarget  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleDataSource::COleDataSource](../Topic/COleDataSource::COleDataSource.md)|构造 `COleDataSource` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleDataSource::CacheData](../Topic/COleDataSource::CacheData.md)|使用 **STGMEDIUM** 结构，提供数据以指定的格式。|  
|[COleDataSource::CacheGlobalData](../Topic/COleDataSource::CacheGlobalData.md)|使用 `HGLOBAL`，提供数据以指定的格式。|  
|[COleDataSource::DelayRenderData](../Topic/COleDataSource::DelayRenderData.md)|采用延迟呈现，提供数据以指定的格式。|  
|[COleDataSource::DelayRenderFileData](../Topic/COleDataSource::DelayRenderFileData.md)|提供数据。在 `CFile` 指针的指定格式。|  
|[COleDataSource::DelaySetData](../Topic/COleDataSource::DelaySetData.md)|调用为 `OnSetData`支持的每个窗体。|  
|[COleDataSource::DoDragDrop](../Topic/COleDataSource::DoDragDrop.md)|执行到数据源的拖放操作。|  
|[COleDataSource::Empty](../Topic/COleDataSource::Empty.md)|空数据 `COleDataSource` 对象。|  
|[COleDataSource::FlushClipboard](../Topic/COleDataSource::FlushClipboard.md)|呈现所有数据添加到剪贴板。|  
|[COleDataSource::GetClipboardOwner](../Topic/COleDataSource::GetClipboardOwner.md)|验证放置在剪贴板上的数据仍然存在。|  
|[COleDataSource::OnRenderData](../Topic/COleDataSource::OnRenderData.md)|为延迟呈现的一部分，检索数据。|  
|[COleDataSource::OnRenderFileData](../Topic/COleDataSource::OnRenderFileData.md)|为延迟呈现的一部分，检索数据。`CFile`。|  
|[COleDataSource::OnRenderGlobalData](../Topic/COleDataSource::OnRenderGlobalData.md)|为延迟呈现的一部分，检索数据。`HGLOBAL`。|  
|[COleDataSource::OnSetData](../Topic/COleDataSource::OnSetData.md)|调用替换为在 `COleDataSource` 对象的数据。|  
|[COleDataSource::SetClipboard](../Topic/COleDataSource::SetClipboard.md)|放置在剪贴板上一 `COleDataSource` 对象。|  
  
## 备注  
 您可以直接创建OLE数据源。  或者，[COleClientItem](../../mfc/reference/coleclientitem-class.md) 和 [COleServerItem](../../mfc/reference/coleserveritem-class.md) 选件类创建OLE数据源以响应其 `CopyToClipboard` 和 `DoDragDrop` 成员函数。  为简短说明参见 [COleServerItem::CopyToClipboard](../Topic/COleServerItem::CopyToClipboard.md)。  重写您的客户端项目或服务器项目选件类的 `OnGetClipboardData` 成员函数添加附加到剪贴板格式为 `CopyToClipboard` 或 `DoDragDrop` 成员函数创建的OLE数据源的数据。  
  
 每当要数据对调用准备，使用您的数据，最合适的方法应创建此选件类对象和用您的数据填充它。  其插入到数据源的方式直接影响是否立即提供该数据\(立即呈现\)或在需要时\(延迟的呈现）。  对于通过将剪贴板格式将要使用的每个剪贴板格式\(和可选 [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) 结构\)提供数据，请调用 [DelayRenderData](../Topic/COleDataSource::DelayRenderData.md)。  
  
 有关数据源和数据传输的更多信息，请参见文章 [数据对象和数据源\(OLE\)](../../mfc/data-objects-and-data-sources-ole.md)。  此外，文章 [剪贴板主题](../../mfc/clipboard.md) 描述OLE剪贴板结构。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDataSource`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [MFC示例HIERSVR](../../top/visual-cpp-samples.md)   
 [MFC示例OCLIENT](../../top/visual-cpp-samples.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDataObject Class](../../mfc/reference/coledataobject-class.md)