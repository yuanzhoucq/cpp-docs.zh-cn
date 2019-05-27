---
title: ATL OLE DB 使用者向导
ms.date: 05/09/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
ms.openlocfilehash: bd7af5c9788f5075f38f85bd035ba8cd09e8baec
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706992"
---
# <a name="atl-ole-db-consumer-wizard"></a>ATL OLE DB 使用者向导

::: moniker range="vs-2019"

此向导不适用于 Visual Studio 2019 及更高版本。

::: moniker-end

::: moniker range="<=vs-2017"

此向导创建 OLE DB 使用者类，其中包含通过指定 OLE DB 提供程序访问指定数据源所需的数据绑定。

> [!NOTE]
> 此向导要求，在“`Class`”和“.h 文件”字段中输入名称前，必须先单击“数据源”按钮来选择数据源。

## <a name="uielement-list"></a>UIElement 列表

- **数据源**

   借助“数据源”按钮，可以使用指定 OLE DB 提供程序来创建指定数据源。 在你单击此按钮后，“数据链接属性”对话框随即出现。 若要详细了解如何生成连接字符串和“数据链接属性”对话框，请参阅 Windows SDK 文档中的[数据链接 API 概述](/previous-versions/windows/desktop/ms718102)。

   以下附加信息描述了“数据链接属性”对话框中的选项卡。

   - “提供程序”选项卡

      选择相应提供程序，以管理与数据源的连接。 提供程序类型通常取决于要连接到的数据库的类型。 单击“下一步”按钮或“连接”选项卡。

   - “连接”选项卡

      此选项卡的内容具体视你选择哪个提供程序而定。 虽然有许多类型的提供程序，但此部分介绍了两种最常见数据的连接：SQL 数据和 ODBC 数据。 其他类型数据就是在下面所述字段的基础上进行类似变体。

      对于 SQL 数据：

      1. **选择或输入服务器名称:** 单击此下拉列表菜单，以显示网络中的所有已注册数据服务器，并选择一个。

      1. **输入登录服务器所需的信息:** 输入用于登录数据服务器的用户名和密码。

         > [!NOTE]
         > “数据链接属性”对话框的“允许保存密码”功能存在安全问题。 在“输入登录服务器所需的信息”中，有两个单选按钮：
         >
         > - **使用 Windows NT 集成安全性**
         > - **使用特定的用户名和密码**
         >
         > 如果选中“使用特定的用户名和密码”，可以视需要保存密码（使用“允许保存密码”复选框），但这样做并不安全。 建议选中“使用 Windows NT 集成安全性”；此选项是安全的，因为它对密码进行加密。
         > 在某些情况下，你可能希望选择“允许保存密码”。 例如，若要将库与专用数据库解决方案一起发布，不得直接访问数据库，而应改用中间层应用程序来验证用户（通过选定的任何身份验证方案），然后限制可供用户使用的数据排序。

      1. **选择服务器上的数据库:** 单击此下拉列表菜单，以显示数据服务器中的所有已注册数据库，并选择一个。

         \- 或 -

         **将数据库文件附加为数据库名称:** 指定要用作数据库的文件；输入显式路径名。

      对于 ODBC 数据：

      1. **指定数据的源:** 可以使用数据源名称或连接字符串。

         **使用数据源名称:** 此下拉列表显示在计算机中注册的数据源。 可以使用 ODBC 数据源管理器提前创建数据源

         \- 或 -

         **使用连接字符串:** 输入已获取的连接字符串，或单击“生成”按钮；此时，“选择数据源”对话框显示。 选择文件或计算机数据源，并单击“确定”。

         > [!NOTE]
         > 可以通过查看“服务器资源管理器”中现有连接的属性来获取连接字符串，也可以通过双击“服务器资源管理器”中的“添加连接”来创建连接。

      1. **输入登录服务器所需的信息:** 输入用于登录数据服务器的用户名和密码。

      1. 输入要使用的初始目录。

      1. 单击“测试连接”；如果测试成功，单击“确定”。 否则，检查登录信息是否正确无误，或尝试另一个数据库或数据服务器。

   - “高级”选项卡

      **网络设置:** 指定“模拟级别”（模拟客户端时服务器可以使用的模拟级别；直接对应于 RPC 模拟级别）和“保护级别”（在客户端和服务器之间发送的数据的保护级别；直接对应于 RPC 保护级别）。

      **其他:** 在“连接超时”中，指定出现多长空闲时间（以秒为单位）算作超时。 在“访问权限”中，指定数据连接的访问权限。

      若要详细了解高级初始化属性，请参阅每个 OLE DB 提供程序随附的文档。

   - “所有”选项卡

      此选项卡汇总了你已指定的数据源和连接的初始化属性。 可以编辑这些值。

      单击“确定”即可完成。 此时，“选择数据库对象”对话框显示。 在此对话框中，选择使用者将使用的表、视图或存储过程。

- **类**

   在你选择数据源后，此框根据你选择的表或存储过程填充有默认类名（请参阅下面的“选择数据源”）。 可以编辑类名。

- **.h 文件**

   在你选择数据源后，此框根据你选择的表或存储过程填充有默认头类名（请参阅下面的“选择数据源”）。 可以编辑头文件名，也可以选择现有头文件。

- **特性化**

   此选项指定向导是使用特性还是使用模板声明来创建使用者类。 如果你选中此选项，向导使用的是特性，而不是模板声明（这是默认选项）。 如果你取消选中此选项，向导使用的是模板声明，而不是特性。

   - 如果你选择“表”作为使用者“类型”，向导使用 `db_source` 和 `db_table` 特性来创建表和表取值函数类声明，并使用 `db_column` 来创建列映射。 例如，它创建以下映射：

        ```cpp
        // Inject table class and table accessor class declarations
        [db_source("<initialization_string>"), db_table("dbo.Orders")]
        ...
        // Column map
        [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
        [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
        ...
        ```

      而不是像下面的示例一样使用 `CTable` 模板类来声明表和表取值函数类，并使用 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 宏来创建列映射：

        ```cpp
        // Table accessor class
            class COrdersAccessor; // Table class
            class COrders : public CTable<CAccessor<COrdersAccessor>>;
        // ...
        // Column map
            BEGIN_COLUMN_MAP(COrderDetailsAccessor)
                COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)
                COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)
                // ...
            END_COLUMN_MAP()
        ```

   - 如果你选择“命令”作为使用者“类型”，向导使用 `db_source` 和 `db_command` 特性，并使用 `db_column` 来创建列映射。 例如，它创建以下映射：

        ```cpp
        [db_source("<initialization_string>"), db_command("SQL_command")]
        ...
        // Column map using db_column is the same as for consumer type of 'table'
        ```

      而不是像下面的示例一样使用命令类 .h 文件中的命令和命令取值函数类声明：

        ```cpp
        // Command accessor class:
            class CListOrdersAccessor;
        // Command class:
            class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
        // ...
        // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
        // for consumer type of 'table'
        ```

      有关详细信息，请参阅[特性的基本机制](../../windows/basic-mechanics-of-attributes.md)。

- **Type**

   选中这些单选按钮之一，可以指定使用者类是派生自 `CTable` 还是派生自 `CCommand`（默认值）。

   - **Table**

      若要使用 `CTable` 或 `db_table` 来创建表和表取值函数类声明，请选中此选项。

   - **命令**

      若要使用 `CCommand` 或 `db_command` 来创建命令和命令取值函数类声明，请选中此选项。 这是默认选项。

- **支持**

   选中复选框可以指定使用者要支持的更新种类（默认值为“无”）。 以下各项会在属性集映射中设置 [DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892)，以及 [DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676) 的相应条目。

   - **更改**

      指定使用者支持更新行集中的行数据。

   - 插入

      指定使用者支持将行插入行集。

   - **删除**

      指定使用者支持从行集中删除行。

::: moniker-end

## <a name="see-also"></a>请参阅

[ATL OLE DB 使用者](../../atl/reference/adding-an-atl-ole-db-consumer.md)<br/>
[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[连接字符串和数据链接 (OLE DB)](/previous-versions/windows/desktop/ms718376)
