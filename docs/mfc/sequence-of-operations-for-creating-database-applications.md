---
title: 用于创建数据库应用程序的操作顺序
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
ms.openlocfilehash: c393269d6af108ee82786e9d59f81aad11428157
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372776"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>用于创建数据库应用程序的操作顺序

下表显示了您在编写数据库应用程序时的角色和框架的作用。

> [!NOTE]
> 可视化C++环境和向导不支持 DAO（尽管包含 DAO 类，您仍可以使用它们）。 Microsoft 建议您将 ODBC 用于新的 MFC 项目。 您只应在维护现有应用程序时使用 DAO。

### <a name="creating-database-applications"></a>创建数据库应用程序

|任务|您执行的操作|框架执行的操作|
|----------|------------|------------------------|
|决定是使用 MFC ODBC 还是 DAO 类。|将 ODBC 用于新的 MFC 项目。 仅使用 DAO 维护现有应用程序。 有关一般信息，请参阅文章["数据访问编程](../data/data-access-programming-mfc-atl.md)"。|框架提供支持数据库访问的类。|
|使用数据库选项创建骨架应用程序。|运行 MFC 应用程序向导。 在"数据库支持"页上选择选项。 如果选择创建记录视图的选项，请指定：<br /><br />- 数据源和表名称或名称<br />- 查询名称或名称。|MFC 应用程序向导创建文件并指定必要的包含。 根据指定的选项，文件可以包括记录集类。|
|设计数据库窗体或表单。|使用可视化C++对话框编辑器在记录视图类的对话框模板资源上放置控件。|MFC 应用程序向导将创建一个空对话框模板资源，供您填写。|
|根据需要创建其他记录视图和记录集类。|使用类视图创建类和对话框编辑器来设计视图。|类视图会为新类创建其他文件。|
|根据需要在代码中创建记录集对象。 使用每个记录集来操作记录...|记录集基于从[CRecordset](../mfc/reference/crecordset-class.md)派生的具有向导的类。|ODBC 使用记录字段交换 （RFX） 在数据库和记录集的字段数据成员之间交换数据。 如果使用记录视图，则对话数据交换 （DDX） 在记录集和记录视图中的控件之间交换数据。|
|...或为要打开的每个数据库在代码中创建显式[CDatabase。](../mfc/reference/cdatabase-class.md)|将记录集对象基于数据库对象。|数据库对象提供数据源的接口。|
|动态地将数据列绑定到记录集。|在 ODBC 中，将代码添加到派生的记录集类以管理绑定。 请参阅文章["记录集：动态绑定数据列 （ODBC）"。](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)||

## <a name="see-also"></a>另请参阅

[基于框架生成](../mfc/building-on-the-framework.md)<br/>
[用于生成 MFC 应用程序的操作顺序](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[创建 OLE 应用程序的操作顺序](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[创建活动X控件的操作顺序](../mfc/sequence-of-operations-for-creating-activex-controls.md)
