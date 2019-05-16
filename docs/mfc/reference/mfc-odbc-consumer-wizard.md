---
title: MFC ODBC 使用者向导
ms.date: 05/09/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 2e8741677031ff9b12989d75243a13550d74b608
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707388"
---
# <a name="mfc-odbc-consumer-wizard"></a>MFC ODBC 使用者向导

::: moniker range="vs-2019"

此向导不是可在 Visual Studio 2019 及更高版本。

::: moniker-end

::: moniker range="<=vs-2017"

此向导设置了 ODBC 记录集类和数据绑定访问指定的数据源所需。

## <a name="uielement-list"></a>UIElement 列表

- **数据源**

  **数据源**按钮的使你可以设置使用指定的 ODBC 驱动程序指定的数据源。 有关数据源文件 (DSN) 的详细信息，请参阅[文件数据源](/sql/odbc/reference/file-data-sources)ODBC SDK 中。

  **选择数据源**对话框有两个选项卡：

  - **文件数据源**选项卡：

     **查找**框指定在其中选择要用作数据源的文件的目录。 默认值为 \Program Files\Common Files\ODBC\Data 源。 在主列表框中显示现有的文件数据源 （.dsn 文件）。 你可以事先使用的数据源设置**文件 DSN**选项卡上[ODBC 数据源管理器](/sql/odbc/admin/odbc-data-source-administrator)，或使用此对话框创建新的。

     若要从该对话框中创建新的文件数据源，请单击`New`指定的 DSN 名称;**创建新的数据源**对话框随即出现。 在中**创建新的数据源**对话框中，选择相应的驱动程序，单击`Next`; 单击**浏览**，并选择要用作数据源 （你需要选择"所有文件"的文件的名称查看非 DSN 文件，如.xls 文件）;单击`Next`，然后单击**完成**。 （如果选择了非 DSN 文件，您将获取特定于驱动程序的对话框中，如"ODBC Microsoft Excel 安装程序，"这会将该文件转换为 DSN）。

     > [!NOTE]
     > 此外可以创建新的文件数据源事先会使用 ODBC 数据源管理器。 从**启动**菜单中，选择**设置**，**控制面板**，**管理工具**，**数据源 (ODBC)**，然后**ODBC 数据源管理器**。

     **DSN 名称**框允许您指定的文件数据源的名称。 您必须确保使用适当的文件扩展名，如 Excel 文件的.xls 或访问文件的.mdb 结束 DSN 名称。

     Dsn 的详细信息，请参阅[文件数据源](/sql/odbc/reference/file-data-sources)ODBC SDK 中。

  - **计算机数据源**选项卡：

     此选项卡列出了系统和用户数据源。 用户数据源是特定于此计算机上的用户。 可以在此计算机上或在系统范围内服务上的所有用户使用系统数据源。 请参阅[机器数据源](/sql/odbc/reference/machine-data-sources)ODBC SDK 中

     有关 ODBC 数据源的详细信息，请参阅[数据源](/sql/odbc/reference/data-sources)ODBC SDK 中。

  单击**确定**来完成。 **选择数据库对象**对话框随即出现。 此对话框，请从选择的表或查看使用者将使用。 请注意，您可以通过单击项时按住控制键选择多个视图和表。 单击**确定**来完成。

- **类**

      The name of the consumer class, based by default on the name of the file or machine data source that you selected.

- **.h 文件**

   使用者类标头文件，默认情况下根据所选的文件或计算机的数据源的名称的名称。

- **.cpp 文件**

   默认情况下根据所选的文件或计算机的数据源的名称的使用者类实现文件的名称。

- **Type**

   指定记录集是动态集 （默认值） 或快照。

   - **动态集**:指定记录集是动态集。 动态集是查询的提供了为查询的数据库的数据的索引的视图的结果。 动态集缓存仅的原始数据的整数索引并提供了一个性能因此获得通过快照。 直接向每个记录的索引点找到作为查询结果，并指示是否删除一条记录。 查询记录中还有权访问更新的信息。 这是默认设置。

   - **快照**:指定记录集是快照。 快照是将查询的结果，并且是时间点上的数据库。 作为查询结果中找到的所有记录会都缓存，因此你看不到对原始记录的任何更改。

- **绑定所有列**

   指定是否绑定中所选表的所有列。 如果选中此框 （默认值），绑定所有列;如果不选择此框，没有列被绑定，并且必须手动在记录集类中绑定。

::: moniker-end

## <a name="see-also"></a>请参阅

[MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)
