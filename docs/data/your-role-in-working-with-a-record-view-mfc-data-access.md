---
title: 你在使用记录视图 （MFC 数据访问） 中的角色 |Microsoft 文档
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
ms.openlocfilehash: e7a9d3fa7e828467e73c77736fb5643baf19660f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111089"
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>你在使用记录视图中的角色（MFC 数据访问）
下表介绍了要处理记录集通常必须执行的操作以及框架的用途。  
  
### <a name="working-with-a-record-view-you-and-the-framework"></a>使用记录视图： 您和框架  
  
|你|框架|  
|---------|-------------------|  
|使用 Visual C++ 对话框编辑器设计窗体。|使用控件创建对话框模板资源。|  
|使用[MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)创建派生自的类[CRecordView](../mfc/reference/crecordview-class.md)和[CRecordset](../mfc/reference/crecordset-class.md)。|编写你的类。|  
|将记录视图控件映射到记录集字段数据成员。|提供控件和记录集字段之间的 DDX。|  
||提供了默认的命令处理程序**移动第一个**，**移动最后一个**，**移动到下一步**，和**移动上一个**从菜单或工具栏上的命令按钮。|  
||更新对数据源的更改。|  
|[可选]编写代码以填充列表框或组合框或包含另一记录集数据的其他控件。||  
|[可选]编写用于任何特殊验证的代码。||  
|[可选]编写代码以添加或删除记录。||  
  
 基于窗体的编程只是处理数据库的一种方法。 有关使用某些其他用户界面或没有用户界面的应用程序的信息，请参阅[MFC： 结合文档和视图使用数据库类](../data/mfc-using-database-classes-with-documents-and-views.md)和[MFC： 使用数据库类不结合文档和视图](../data/mfc-using-database-classes-without-documents-and-views.md). 有关显示数据库记录的其他方法，请参阅类[CListView](../mfc/reference/clistview-class.md)和[CTreeView](../mfc/reference/ctreeview-class.md)。  
  
## <a name="see-also"></a>请参阅  
 [记录视图 （MFC 数据访问）](../data/record-views-mfc-data-access.md)   
 [ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)