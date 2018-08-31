---
title: 使用 OLE DB 记录视图 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b0b787686fc09d943de030645d56465cd259bc37
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215762"
---
# <a name="using-ole-db-record-views"></a>使用 OLE DB 记录视图
如果你想要在 MFC 应用程序中显示 OLE DB 行集数据，则应使用 MFC 类[COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)。 从创建记录视图对象`COleDBRecordView`使你可以在 MFC 控件中显示数据库记录。 记录视图是直接连接到从创建的 OLE DB 行集对象的对话框窗体视图`CRowset`模板类。 获取行集对象的句柄很简单：  
  
```cpp  
COleDBRecordView myRecordView;  
...  
// CProductAccessor is a user record class  
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();  
```  
  
 该视图显示字段的`CRowset`对话框的控件中的对象。 `COleDBRecordView`对象使用对话框数据交换 (DDX) 和导航功能内置到`CRowset`(`MoveFirst`， `MoveNext`， `MovePrev`，并`MoveLast`) 来自动执行窗体上控件之间的数据移动和行集的字段。 `COleDBRecordView` 跟踪的行集中的用户的位置，以便记录视图可以更新用户界面和耗材[OnMove](../../mfc/reference/coledbrecordview-class.md#onmove)之前转移到另一个更新的当前记录的方法。  
  
 您可以使用 DDX 函数与`COleDbRecordView`以直接从数据库记录集获取数据并将其显示在对话框控件。 应使用**DDX_** <strong>\*</strong>方法 (如`DDX_Text`)，而不**DDX_Field** <strong>\*</strong>函数 (如`DDX_FieldText`) 与`COleDbRecordView`。  
  
## <a name="see-also"></a>请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)   
 [COleDBRecordView 类](../../mfc/reference/coledbrecordview-class.md)