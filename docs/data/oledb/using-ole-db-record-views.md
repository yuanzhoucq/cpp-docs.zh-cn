---
title: "使用 OLE DB 记录视图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 03e88eaafa82e346c720810bf567d867a9cd6096
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-ole-db-record-views"></a>使用 OLE DB 记录视图
如果你想要在 MFC 应用程序中显示 OLE DB 行集数据，则应使用 MFC 类[COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)。 从创建记录视图对象`COleDBRecordView`使你可以在 MFC 控件中显示数据库记录。 记录视图是直接连接到从创建的 OLE DB 行集对象的对话框窗体视图`CRowset`模板类。 获取行集对象的句柄很简单：  
  
```  
COleDBRecordView myRecordView;  
...  
// CProductAccessor is a user record class  
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();  
```  
  
 视图显示的字段`CRowset`对话框的控件中的对象。 `COleDBRecordView`对象使用对话框数据交换 (DDX) 和导航功能内置于`CRowset`(**MoveFirst**， `MoveNext`， `MovePrev`，和`MoveLast`) 以自动进行的数据移动之间在窗体和行集的字段的控件。 `COleDBRecordView`将跟踪的行集中的用户的位置，以便记录视图可以更新用户界面并提供[OnMove](../../mfc/reference/coledbrecordview-class.md#onmove)再转移到另一个更新当前记录方法。  
  
 您可以使用与的 DDX 函数**COleDbRecordView**直接从数据库记录集获取数据并将其显示在对话框控件。 应使用**DDX_\*** 方法 (如`DDX_Text`)，而不**DDX_Field\*** 函数 (如`DDX_FieldText`) 与**COleDbRecordView**.  
  
## <a name="see-also"></a>请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)   
 [COleDBRecordView 类](../../mfc/reference/coledbrecordview-class.md)