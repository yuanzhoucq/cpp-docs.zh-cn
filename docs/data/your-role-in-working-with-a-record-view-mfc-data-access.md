---
title: 在使用记录视图 （MFC 数据访问） 中的角色 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f0188f9b7498bc704c43f642fcb7aa1dc72af6a4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105461"
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>你在使用记录视图中的角色（MFC 数据访问）

下表介绍了要处理记录集通常必须执行的操作以及框架的用途。  
  
### <a name="working-with-a-record-view-you-and-the-framework"></a>使用记录视图： 你和框架  
  
|你|框架|  
|---------|-------------------|  
|使用 Visual C++ 对话框编辑器设计窗体。|使用控件创建对话框模板资源。|  
|使用[MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)来创建类派生自[CRecordView](../mfc/reference/crecordview-class.md)并[CRecordset](../mfc/reference/crecordset-class.md)。|编写你的类。|  
|将记录视图控件映射到记录集字段数据成员。|提供控件和记录集字段之间的 DDX。|  
||提供用于命令处理程序的默认**移动第一个**，**移到最后**，**移动到下一步**，并**移动上一个**菜单或工具栏中的命令按钮。|  
||更新对数据源的更改。|  
|[可选]编写代码以填充列表框或组合框或包含另一记录集数据的其他控件。||  
|[可选]编写用于任何特殊验证的代码。||  
|[可选]编写代码以添加或删除记录。||  
  
基于窗体的编程只是处理数据库的一种方法。 有关使用其他用户界面或没有用户界面的应用程序的信息，请参阅[MFC： 结合文档和视图使用数据库类](../data/mfc-using-database-classes-with-documents-and-views.md)和[MFC： 使用数据库类不结合文档和视图](../data/mfc-using-database-classes-without-documents-and-views.md). 显示数据库记录的替代方法，请参见类[CListView](../mfc/reference/clistview-class.md)并[CTreeView](../mfc/reference/ctreeview-class.md)。  
  
## <a name="see-also"></a>请参阅  

[记录视图（MFC 数据访问）](../data/record-views-mfc-data-access.md)<br/>
[ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)