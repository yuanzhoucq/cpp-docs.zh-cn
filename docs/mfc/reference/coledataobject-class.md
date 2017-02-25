---
title: "COleDataObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IDataObject"
  - "COleDataObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "剪贴板 [C++], MFC 支持"
  - "剪贴板 [C++], OLE 支持"
  - "COleDataObject class"
  - "data transfer [C++]"
  - "data transfer [C++], OLE"
  - "drag and drop [C++], MFC 支持"
  - "IDataObject interface, MFC encapsulation"
  - "OLE [C++], uniform data transfer"
  - "OLE Clipboard [C++], 支持"
  - "OLE data transfer [C++]"
  - "uniform data transfer"
  - "uniform data transfer, OLE"
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# COleDataObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用在数据传输提供用于检索数据的各种格式从剪贴板，通过拖放，或者从嵌入式OLE项。  
  
## 语法  
  
```  
class COleDataObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleDataObject::COleDataObject](../Topic/COleDataObject::COleDataObject.md)|构造 `COleDataObject` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleDataObject::Attach](../Topic/COleDataObject::Attach.md)|附加到 `COleDataObject`的指定OLE的数据对象。|  
|[COleDataObject::AttachClipboard](../Topic/COleDataObject::AttachClipboard.md)|将剪贴板中的数据对象。|  
|[COleDataObject::BeginEnumFormats](../Topic/COleDataObject::BeginEnumFormats.md)|为一个或多个后续 `GetNextFormat` 准备调用。|  
|[COleDataObject::Detach](../Topic/COleDataObject::Detach.md)|分离关联的 `IDataObject` 对象。|  
|[COleDataObject::GetData](../Topic/COleDataObject::GetData.md)|将附加的OLE的数据对象的数据以指定的格式。|  
|[COleDataObject::GetFileData](../Topic/COleDataObject::GetFileData.md)|将附加的OLE的数据对象的数据绑定到一 `CFile` 指针以指定的格式。|  
|[COleDataObject::GetGlobalData](../Topic/COleDataObject::GetGlobalData.md)|将附加的OLE的数据对象的数据。`HGLOBAL` 以指定的格式。|  
|[COleDataObject::GetNextFormat](../Topic/COleDataObject::GetNextFormat.md)|返回下一个可用的数据格式。|  
|[COleDataObject::IsDataAvailable](../Topic/COleDataObject::IsDataAvailable.md)|检查数据是否可用在指定的格式。|  
|[COleDataObject::Release](../Topic/COleDataObject::Release.md)|分离并释放关联的 `IDataObject` 对象。|  
  
## 备注  
 `COleDataObject` 没有基类。  
  
 这些数据传输包括一个源和一个目标。  数据源实现为 [COleDataSource](../../mfc/reference/coledatasource-class.md) 选件类的对象。  只要目标应用程序具有放置的数据。它或请求的状态从剪贴板中粘贴操作，必须创建 `COleDataObject` 选件类的对象。  
  
 此选件类可确定数据是否存在以指定的格式。  也可以枚举可用数据格式或检查特定格式是否可用然后检索数据以首选格式。  对象检索可完成以多种不同的方式，包括使用 [C文件](../../mfc/reference/cfile-class.md)、 `HGLOBAL`或 **STGMEDIUM** 结构。  
  
 有关更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) 结构。  
  
 有关使用数据对象的更多信息在您的应用程序，请参见文章 [数据对象和数据源\(OLE\)](../../mfc/data-objects-and-data-sources-ole.md)。  
  
## 继承层次结构  
 `COleDataObject`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [MFC示例HIERSVR](../../top/visual-cpp-samples.md)   
 [MFC示例OCLIENT](../../top/visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDataSource Class](../../mfc/reference/coledatasource-class.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)   
 [COleDataSource::DoDragDrop](../Topic/COleDataSource::DoDragDrop.md)   
 [CView::OnDrop](../Topic/CView::OnDrop.md)