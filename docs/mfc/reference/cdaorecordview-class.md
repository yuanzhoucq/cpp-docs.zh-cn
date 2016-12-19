---
title: "CDaoRecordView Class | Microsoft Docs"
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
  - "CDaoRecordView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序向导 [C++], creating record views"
  - "绑定控件 [C++], displaying database data"
  - "CDaoRecordView 类"
  - "控件 [MFC], data binding"
  - "数据绑定 [C++], DAO views"
  - "数据绑定控件 [C++], DAO 控件"
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoRecordView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

显示控件中数据库记录的视图。  
  
## 语法  
  
```  
  
class AFX_NOVTABLE CDaoRecordView : public CFormView  
  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDaoRecordView::CDaoRecordView](../Topic/CDaoRecordView::CDaoRecordView.md)|构造 `CDaoRecordView` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDaoRecordView::IsOnFirstRecord](../Topic/CDaoRecordView::IsOnFirstRecord.md)|如果当前记录位于关联的记录集，的第一条记录返回非零。|  
|[CDaoRecordView::IsOnLastRecord](../Topic/CDaoRecordView::IsOnLastRecord.md)|如果当前记录位于关联的记录集，中的最后一条记录返回非零。|  
|[CDaoRecordView::OnGetRecordset](../Topic/CDaoRecordView::OnGetRecordset.md)|返回指向 `CDaoRecordset`从派生的选件类的对象。  类向导会重写您的此功能，并根据需要创建记录集。|  
|[CDaoRecordView::OnMove](../Topic/CDaoRecordView::OnMove.md)|如果当前记录已更改，更新其在数据源，则将改为指定的记录\(接下来，前面的中，第一个字节\(前）。|  
  
## 备注  
 视图是窗体视图直接连接到 `CDaoRecordset` 对象。  视图由对话框模板资源创建并显示 `CDaoRecordset` 对象的字段在对话框模板的控件中。  `CDaoRecordView` 对象使用对话框数据交换\(ddx\)和DAO记录字段交换\(DFX\)自动数据移动到的控件在窗体和记录集之间的字段。  `CDaoRecordView` 还提供对移动的默认实现\)到第一，接下来，条、最后一条记录和一个接口当前更新的记录视图中。  
  
> [!NOTE]
>  DAO数据库选件类根据了开放式数据库连接的MFC数据库选件类都一目了然\(odbc）。  所有DAO数据库类名具有“CDao”前缀。  您仍然可以访问使用DAO选件类的ODBC数据源;，因为它们使用Microsoft Jet数据库引擎，DAO选件类通常提供优越功能。  
  
 最常见的方式创建记录视图是使用应用程序向导。  为主干起始应用程序的一部分，应用程序向导创建两个记录视图选件类及其关联的记录集选件类。  
  
 如果需要单个窗体，应用程序向导方法更加容易。  类向导在允许您决定使用记录视图后开发过程。  如果您使用应用程序向导不创建记录视图选件类，可以使用类向导之后创建它。  使用类向导单独创建记录视图和记录集连接到它们是最灵活的方法，因为它为您在命名选件记录集类的更多控件及其。H\/.CPP文件。  此方法还允许您在同一记录集选件类的多个记录视图。  
  
 为了方便最终用户将从记录到记录视图的记录，应用程序向导创建的移动到第一个，接下来，条、最后一条记录的菜单\(并且可以是工具栏\)的资源。  如果使用类向导创建记录视图选件类，需要使用菜单和位图编辑器创建这些资源。  
  
 有关移动的默认实现的信息从记录到日志，请参见 `IsOnFirstRecord` 和 `IsOnLastRecord` 和文章 [使用记录视图](../../data/using-a-record-view-mfc-data-access.md)，适用于 `CRecordView` 和 `CDaoRecordView`。  
  
 `CDaoRecordView` 记录在记录集的用户的位置，以便记录视图能够更新用户界面。  当用户移动到记录集中的任一端，记录视图禁用用户界面对象\(如菜单项或工具栏按钮—操作的进一步沿相同的方向。  
  
 有关声明和使用您的记录视图和记录集选件类的更多信息，请参见的“设计和创建记录视图”。这篇文章 [记录视图](../../data/record-views-mfc-data-access.md)上。  有关记录视图的工作原理以及如何使用它们的更多信息，请参见文章 [使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。  上面提到的所有文章适用于 `CRecordView` 和 `CDaoRecordView`。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CDaoRecordView`  
  
## 要求  
 **Header:** afxdao.h  
  
## 请参阅  
 [CFormView Class](../../mfc/reference/cformview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)