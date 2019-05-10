---
title: 用于创建数据库应用程序的操作顺序
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
ms.openlocfilehash: efd6b12b186ce0ef1c0caf57f313f6aa50425fec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308493"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>用于创建数据库应用程序的操作顺序

下表显示你的角色和框架的角色中编写数据库应用程序。

> [!NOTE]
>  视觉对象C++环境和向导不支持 DAO （尽管 DAO 类包含并且仍可以使用它们）。 Microsoft 建议为新 MFC 项目使用 ODBC。 仅应在维护现有应用程序使用 DAO。

### <a name="creating-database-applications"></a>创建数据库应用程序

|任务|您执行的操作|框架执行的操作|
|----------|------------|------------------------|
|决定是否使用 MFC ODBC 或 DAO 类。|为新 MFC 项目中使用 ODBC。 使用 DAO 只是为了维护现有的应用程序。 有关常规信息，请参阅文章[数据访问编程](../data/data-access-programming-mfc-atl.md)。|框架提供了支持数据库访问权限的类。|
|使用数据库选项创建主干应用程序。|运行 MFC 应用程序向导。 选择数据库支持页面上的选项。 如果您选择创建记录视图的选项，还指定：<br /><br />数据源和表名称或名称<br />-查询名称。|MFC 应用程序向导创建的文件，并指定所需包括。 根据你指定的选项，这些文件可以包括一个记录集类。|
|设计数据库窗体或窗体。|使用视觉对象C++对话框编辑器将记录视图类的对话框模板资源上的控件。|MFC 应用程序向导创建你可填写空对话框模板资源。|
|根据需要创建其他记录的视图和记录集类。|使用类视图创建的类和对话框编辑器设计视图。|类视图创建新类的其他的文件。|
|根据需要在代码中创建记录集对象。 每个记录集用于处理记录...|在记录集都基于派生自的类[CRecordset](../mfc/reference/crecordset-class.md)使用向导。|ODBC 使用记录字段交换 (RFX) 数据库和记录集的字段数据成员之间交换数据。 如果使用记录视图，对话框数据交换 (DDX) 之间交换数据记录集和记录视图上的控件。|
|...或创建一个显式[CDatabase](../mfc/reference/cdatabase-class.md)代码中的每个你想要打开的数据库。|记录集对象基于的数据库对象。|数据库对象提供对数据源的接口。|
|动态绑定到记录集的数据列。|在 ODBC 中，将代码添加到派生的记录集类，以管理绑定。 请参阅文章[记录集：动态绑定数据列 (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。||

## <a name="see-also"></a>请参阅

[基于框架生成](../mfc/building-on-the-framework.md)<br/>
[MFC 应用程序的构建操作顺序](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[OLE 应用程序的创建操作顺序](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[ActiveX 控件的创建操作顺序](../mfc/sequence-of-operations-for-creating-activex-controls.md)
