---
title: "用于创建数据库应用程序的操作顺序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f3403807e38f59abc68bf93f510476951c5ec8ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>用于创建数据库应用程序的操作顺序
下表显示你的角色和框架的角色中编写数据库应用程序。  
  
> [!NOTE]
>  Visual c + + 环境和向导不支持 DAO （尽管 DAO 类包括并且仍可以使用它们）。 Microsoft 建议你为新 MFC 项目使用 ODBC。 你只应在维护现有应用程序使用 DAO。  
  
### <a name="creating-database-applications"></a>创建数据库应用程序  
  
|任务|您执行的操作|框架执行的操作|  
|----------|------------|------------------------|  
|决定是否使用 MFC ODBC 或 DAO 类。|为新 MFC 项目中使用 ODBC。 使用 DAO 只是为了维护现有应用程序。 有关常规信息，请参阅文章[数据访问编程](../data/data-access-programming-mfc-atl.md)。|框架提供了支持数据库访问的类。|  
|使用数据库选项创建主干应用程序。|运行 MFC 应用程序向导。 选择数据库支持页上的选项。 如果你选择一个选项，创建记录视图，还指定：<br /><br /> 数据源和表名称或名称<br />-查询名称。|MFC 应用程序向导创建文件，并指定所需包括。 根据你指定的选项，该文件可以包括记录集类。|  
|设计数据库窗体或窗体。|使用 Visual c + + 对话框编辑器将记录视图类的对话框模板资源上的控件。|MFC 应用程序向导创建你填写空对话框模板资源。|  
|根据需要创建其他记录的视图和记录集类。|使用类视图创建的类和对话框编辑器设计视图。|类视图创建新类的其他文件。|  
|根据需要在你的代码，请创建记录集对象。 使用每个记录集来操作记录...|你的记录集都基于派生自的类[CRecordset](../mfc/reference/crecordset-class.md)使用向导。|ODBC 使用记录字段交换 (RFX) 数据库和记录集的字段数据成员之间交换数据。 如果使用记录视图，对话框数据交换 (DDX) 之间交换数据的记录集和记录视图上的控件。|  
|...或创建显式[CDatabase](../mfc/reference/cdatabase-class.md)你想要打开每个数据库在代码中。|基础记录集对象上的数据库对象。|数据源为接口提供的数据库对象。|  
|动态绑定到记录集的数据列。|ODBC，在添加到你派生的记录集类，以管理绑定的代码。 请参阅文章[记录集： 动态绑定数据列 (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。||  
  
## <a name="see-also"></a>请参阅  
 [基于框架生成](../mfc/building-on-the-framework.md)   
 [用于生成 MFC 应用程序的操作顺序](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [用于创建 OLE 应用程序的操作顺序](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [ActiveX 控件的创建操作顺序](../mfc/sequence-of-operations-for-creating-activex-controls.md)
