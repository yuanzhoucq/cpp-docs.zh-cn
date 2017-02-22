---
title: "COleDBRecordView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDBRecordView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDBRecordView 类"
  - "MFC, OLE DB"
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# COleDBRecordView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

显示控件中数据库记录的视图。  
  
## 语法  
  
```  
class COleDBRecordView : public CFormView  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleDBRecordView::COleDBRecordView](../Topic/COleDBRecordView::COleDBRecordView.md)|构造 `COleDBRecordView` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleDBRecordView::OnGetRowset](../Topic/COleDBRecordView::OnGetRowset.md)|返回一个标准 `HRESULT` 值。|  
|[COleDBRecordView::OnMove](../Topic/COleDBRecordView::OnMove.md)|更新当前记录（如果有）在数据源然后将更改为指定的记录\(接下来，前面的中，第一个字节\(前）。|  
  
## 备注  
 视图是窗体视图直接连接到 `CRowset` 对象。  视图由对话框模板资源创建并显示 `CRowset` 对象的字段在对话框模板的控件中。  `COleDBRecordView` 对象使用对话框数据交换\(ddx\)和内置的导航功能 `CRowset`，自动数据移动到的控件在窗体和行集合之间的字段。  `COleDBRecordView` 还提供对移动的默认实现\)到第一，接下来，条、最后一条记录和一个接口当前更新的记录在视图。  
  
 可以将 DDX 功能与 **COleDbRecordView** 一起使用，以便直接从数据库记录集中获取数据，并在对话框控件中显示它。  应将 **DDX\_\*** 方法（如 `DDX_Text`）而不是 **DDX\_Field\*** 函数（如 `DDX_FieldText`）与 **COleDbRecordView** 一起使用。  `DDX_FieldText` 不会使用 **COleDbRecordView** 一起使用，因为 `DDX_FieldText` 采用类型 **CRecordset\*** \(对于 `CRecordView`\)或 **CDaoRecordset\*** 的其他参数\(对于 `CDaoRecordView`）。  
  
> [!NOTE]
>  如果您使用的是数据访问使用否决\(DAO\)选件类而不是OLE DB使用者模板选件类，使用选件类 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)。  有关更多信息，请参见文章 [概述:数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
 `COleDBRecordView` 记录行集合中的用户的位置，以便记录视图能够更新用户界面。  当用户移到行集合中的任一端，记录视图禁用用户界面对象\(如菜单项或工具栏按钮—操作的进一步沿相同的方向。  
  
 有关行集合选件类的更多信息，请参见 [使用OLE DB使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md) 文章。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `COleDBRecordView`  
  
## 要求  
 **Header:** afxoledb.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)