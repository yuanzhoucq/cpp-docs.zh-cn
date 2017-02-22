---
title: "CRecordView 和 CDaoRecordView 的对话框数据交换函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO [C++], 对话框数据交换 (DDX) 支持"
  - "数据库 [C++], 对话框数据交换 (DDX) 支持"
  - "DDX（对话框数据交换）[C++], 数据库支持"
  - "DDX（对话框数据交换）[C++], 函数"
  - "DDX_Field 函数"
  - "ODBC [C++], 对话框数据交换 (DDX) 支持"
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CRecordView 和 CDaoRecordView 的对话框数据交换函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题列出 DDX\_Field 函数用于在 [CRecordset](../../mfc/reference/crecordset-class.md) 和[CRecordView](../../mfc/reference/crecordview-class.md) 窗体之间或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 窗体之间交换数据。  
  
> [!NOTE]
>  DDX\_Field函数与 DDX函数相似，在窗体中交换控件数据。  但是，与 DDX不同的是，DDX\_Field函数是与视图关联的记录集对象的字段交换数据，而不是与记录视图本身的字段。  有关详细信息，请参阅`CRecordView` 和 `CDaoRecordView`.。  
  
### DDX\_Field 函数  
  
|||  
|-|-|  
|[DDX\_FieldCBIndex](../Topic/DDX_FieldCBIndex.md)|在[CRecordView](../../mfc/reference/crecordview-class.md) 或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)中，传输记录集字段数据成员和组合框中当前选定内容的整数。|  
|[DDX\_FieldCBString](../Topic/DDX_FieldCBString.md)|在 `CRecordView` 或 `CDaoRecordView`中，传输记录集字段数据成员和一个组合框的编辑控件之间的 `CString` 数据。  如果把记录集的数据移到控件，此函数中选择以在指定字符串的字符开头的组合框中的项。|  
|[DDX\_FieldCBStringExact](../Topic/DDX_FieldCBStringExact.md)|在 `CRecordView` 或 `CDaoRecordView`中，传输记录集字段数据成员和一个组合框的编辑控件之间的 `CString` 数据。  如果将记录集的数据移到控件，此函数选择在与指定字符的组合框中的项。|  
|[DDX\_FieldCheck](../Topic/DDX_FieldCheck.md)|在`CRecordView` 或 `CDaoRecordView`中，传输记录集字段数据成员和复选框之间的布尔数据。|  
|[DDX\_FieldLBIndex](../Topic/DDX_FieldLBIndex.md)|在`CRecordView` 或 `CDaoRecordView`中，传输记录集字段数据成员和组合框中当前选定内容的整数。|  
|[DDX\_FieldLBString](../Topic/DDX_FieldLBString.md)|在列表框控件和记录集的字段数据成员之间管理 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 数据传输。  如果把记录集的数据移到控件，此函数中选择以在指定字符串的字符开头的列表框中的项。|  
|[DDX\_FieldLBStringExact](../Topic/DDX_FieldLBStringExact.md)|在列表框控件和记录集的字段数据成员之间管理  `CString` 数据传输。  如果将记录集的数据移到控件，此函数选择与指定字符完全符合的第一项。|  
|[DDX\_FieldRadio](../Topic/DDX_FieldRadio.md)|在 `CRecordView` 或 `CDaoRecordView`中，传输记录集字段数据成员和一组单选按钮之间的整数数据。|  
|[DDX\_FieldScroll](../Topic/DDX_FieldScroll.md)|设置或获取滚动条控件的滚动位置，在`CRecordView` 或 `CDaoRecordView`中。  从 [DoFieldExchange](../Topic/CDaoRecordset::DoFieldExchange.md) 函数调用。|  
|[DDX\_FieldText](../Topic/DDX_FieldText.md)|在`CRecordView` 或 `CDaoRecordView`中，重载版本适用于在记录集字段数据成员和编辑框中传输 `int`、**UINT**、**long**、`DWORD`、[CString](../../atl-mfc-shared/reference/cstringt-class.md)、**float**、**double**、**short**、[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)和 [COleCurrency](../../mfc/reference/colecurrency-class.md) 数据。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)