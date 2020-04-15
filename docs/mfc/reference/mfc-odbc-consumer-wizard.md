---
title: MFC ODBC 使用者向导
ms.date: 08/29/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 45087434c0093f99383096761d58a8029c9d5009
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373022"
---
# <a name="mfc-odbc-consumer-wizard"></a>MFC ODBC 使用者向导

::: moniker range="vs-2019"

此向导不适用于 Visual Studio 2019 及更高版本。

::: moniker-end

::: moniker range="<=vs-2017"

此向导设置 ODBC 记录集类以及访问指定数据源所需的数据绑定。

## <a name="uielement-list"></a>UIElement 列表

- **数据源**

  通过 **"数据源**"按钮，您可以使用指定的 ODBC 驱动程序设置指定的数据源。 有关数据源文件 （DSN） 的详细信息，请参阅 ODBC SDK 中[的文件数据源](/sql/odbc/reference/file-data-sources)。

  "**选择数据源**"对话框有两个选项卡：

  - **文件数据源**选项卡：

     "**查看"** 框指定选择要用作数据源的文件的目录。 默认值为 [程序文件]公共文件\ODBC_数据源。 现有文件数据源 （.dsn 文件） 将显示在主列表框中。 您可以使用[ODBC 数据源管理员](/sql/odbc/admin/odbc-data-source-administrator)上**的文件 DSN**选项卡提前设置数据源，也可以使用此对话框创建新数据源。

     要从此对话框创建新的文件数据源，请单击以指定 DSN 名称;单击以指定`New`DSN 名称。将显示"**创建新数据源"** 对话框。 在 **"创建新数据源"** 对话框中，选择适当的驱动程序并单击`Next`""。单击 **"浏览**"并选择用作数据源的文件的名称（您必须选择"所有文件"才能查看非 DSN 文件，如 .xls 文件）;单击`Next`，然后单击 **"完成**"。 （如果选择了非 DSN 文件，您将获得特定于驱动程序的对话框，例如"ODBC 微软 Excel 设置"，该对话框会将文件转换为 DSN。

     > [!NOTE]
     > 您还可以使用 ODBC 数据源管理员提前创建新的文件数据源。 在 **"开始"** 菜单中，选择 **"设置**"、"**控制面板**"、"**管理工具**"、"**数据源 "（ODBC），** 然后**选择 ODBC 数据源管理员**。

     **DSN 名称**框允许您为文件数据源指定名称。 必须确保 DSN 名称以适当的文件扩展名结束，例如 Excel 文件的 .xls 或 Access 文件的 .mdb。

     有关 DSN 的详细信息，请参阅 ODBC SDK 中[的文件数据源](/sql/odbc/reference/file-data-sources)。

  - **计算机数据源**选项卡：

     此选项卡列出了系统和用户数据源。 用户数据源特定于此计算机上的用户。 系统数据源可以由此计算机上的所有用户或系统范围的服务使用。 请参阅 ODBC SDK 中的[机器数据源](/sql/odbc/reference/machine-data-sources)

     有关 ODBC 数据源的详细信息，请参阅 ODBC SDK 中的[数据源](/sql/odbc/reference/data-sources)。

  单击“确定”**** 以完成操作。 此时，“选择数据库对象”**** 对话框显示。 在此对话框中，选择使用者将使用的表或视图。 请注意，在单击项目时，可以通过按住控制键来选择多个视图和表。 单击“确定”**** 以完成操作。

- **类**

   使用者类的名称，默认情况下基于您选择的文件或计算机数据源的名称。

- **.h 文件**

   使用者类标头文件的名称，默认情况下基于您选择的文件或计算机数据源的名称。

- **.cpp 文件**

   使用者类实现文件的名称，默认情况下基于您选择的文件或计算机数据源的名称。

- **Type**

   指定记录集是动态集（默认）还是快照。

  - **动态集**：指定记录集是动态集。 动态集是查询的结果，该查询向查询数据库的数据提供索引视图。 动态集仅缓存原始数据的整体索引，因此比快照提供性能提升。 索引直接指向查询结果找到的每个记录，并指示是否删除了记录。 您还可以访问查询记录中的更新信息。 这是默认值。

  - **快照**：指定记录集是快照。 快照是查询的结果，是某个时间点对数据库的视图。 查询结果找到的所有记录都将被缓存，因此您看不到对原始记录的任何更改。

- **绑定所有列**

   指定是否绑定所选表中的所有列。 如果选择此框（默认值），则所有列都绑定;如果选择此框（默认值），则所有列都绑定。如果不选择此框，则不会绑定任何列，并且必须在记录集类中手动绑定它们。

::: moniker-end

## <a name="see-also"></a>另请参阅

[MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)
