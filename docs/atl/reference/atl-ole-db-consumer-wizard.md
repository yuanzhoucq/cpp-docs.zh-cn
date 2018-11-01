---
title: ATL OLE DB 使用者向导
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.consumer.overview
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- connection strings [C++], OLE DB consumers
- ATL OLE DB Consumer Wizard
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
ms.openlocfilehash: 835b3e6246741c3859f51e017686531f450db194
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499562"
---
# <a name="atl-ole-db-consumer-wizard"></a>ATL OLE DB 使用者向导

此向导设置 OLE DB 使用者类使用的数据绑定通过指定 OLE DB 访问接口访问指定的数据源所需。

> [!NOTE]
> 此向导需要单击**数据源**按钮以选择数据源中输入名称之前`Class`并 **.h 文件**字段。

## <a name="uielement-list"></a>UIElement 列表

- **数据源**

   **数据源**按钮的使你可以设置使用指定的 OLE DB 访问接口的指定的数据源。 单击此按钮时**数据链接属性**对话框随即出现。 有关详细信息生成连接字符串和**数据链接属性**对话框中，请参阅[数据链接 API 概述](/previous-versions/windows/desktop/ms718102)Windows SDK 文档中。

   以下附加信息描述了中的选项卡**数据链接属性**对话框。

   - **提供程序**选项卡

      选择相应的提供程序来管理与数据源的连接。 提供程序的类型通常是取决于要连接到数据库的类型。 单击**下一步**按钮或单击**连接**选项卡。

   - **连接**选项卡

      此选项卡的内容取决于所选的提供程序。 虽然有许多类型的提供程序，但本部分介绍了连接的两个最常见： SQL 和 ODBC 的数据。 其他类型是类似的变体此处所述的字段。

      对于 SQL 数据：

      1. **选择或输入服务器名称：** 单击要显示所有已注册的数据服务器在网络上的下拉列表菜单，然后选择一个。

      1. **输入登录到服务器上的信息：** 输入用户名和密码登录到数据服务器上。

         > [!NOTE]
         > 没有与数据链接属性对话框中的"允许保存密码"功能的安全问题。 在"输入信息以登录到服务器上，"有两个单选按钮：
         >
         > - **使用 Windows NT 集成安全性**
         > - **使用特定用户名和密码**
         >
         > 如果选择**使用特定用户名和密码**，可以选择保存密码 （使用"允许保存密码"复选框）; 但是，此选项是不安全。 我们建议您选择**使用 Windows NT 集成安全性**; 此选项不安全，因为它对密码进行加密。
         > 有时可能想要选择"允许保存密码"。 例如，如果发布具有专用的数据库解决方案的库，您应直接访问数据库而应该使用的中间层应用程序若要验证的用户 （通过选择任何身份验证方案），然后限制的数据排序可供用户使用。

      1. **选择在服务器上的数据库：** 单击要显示所有已注册的数据库数据服务器上的下拉列表菜单，然后选择一个。

         \- 或 -

         **附加数据库文件作为数据库名称：** 指定要用作数据库的文件; 输入显式路径名。

      对于 ODBC 数据：

      1. **指定数据源：** 可以使用数据源名称或连接字符串。

         **使用数据源名称：** 此下拉列表显示在计算机中注册的数据源。 您可以设置提前使用 ODBC 数据源管理器数据源

         \- 或 -

         **使用连接字符串：** 输入连接字符串已获取，或单击**构建**按钮;**选择数据源**对话框随即出现。 选择文件或计算机的数据源，然后单击**确定**。

         > [!NOTE]
         > 可以通过查看中的现有连接的属性获取的连接字符串**服务器资源管理器**，也可以通过双击创建连接**添加连接**中**服务器资源管理器**。

      1. **输入登录到服务器上的信息：** 输入用户名和密码登录到数据服务器上。

      1. 输入要使用的初始目录。

      1. 单击**测试连接**; 如果测试成功，单击**确定**。 如果没有，检查您的登录信息，请尝试另一个数据库，或尝试另一个数据服务器。

   - **高级**选项卡

      **网络设置：** 指定**模拟级别**（的服务器可以模拟客户端时使用; 直接对应于 RPC 模拟级别的模拟级别） 和**保护级别**（客户端和服务器之间发送的数据的保护级别对应直接到 RPC 保护级别）。

      **其他：** 中**连接超时**，指定发生超时之前允许的空闲时间的秒数。 在中**访问权限**，在数据连接上指定的访问权限。

       有关高级的初始化属性的详细信息，请参阅每个特定的 OLE DB 访问接口提供的文档。

   - **所有**选项卡

      此选项卡显示的数据源和具有指定的连接的初始化属性的摘要。 你可以编辑这些值。

   单击**确定**来完成。 **选择数据库对象**对话框随即出现。 从该对话框中，选择表、 视图或使用者将使用的存储的过程。

- **类**

   选择数据源后，使用基于的表或您选择的存储的过程的默认类名称填充此框 (请参阅**选择数据源**下面)。 您可以编辑类名称。

- **.h 文件**

   选择数据源后，使用基于的表或您选择的存储的过程的默认标头类名称填充此框 (请参阅**选择数据源**下面)。 可以编辑该标头文件的名称，也可以选择现有的头文件。

- **特性化**

   此选项指定向导是否将创建使用者使用属性或模板声明的类。 在选择此选项，该向导使用特性而不是模板声明 （这是默认选项）。 当取消选择此选项时，向导使用模板声明而不是属性。

   - 如果选择使用者**类型**的**表**，则向导将使用`db_source`并`db_table`属性来创建表和表访问器类声明中，并使用`db_column`到创建列映射。 例如，它将创建此映射：

        ```cpp
        // Inject table class and table accessor class declarations
        [db_source("<initialization_string>"), db_table("dbo.Orders")]
        ...
        // Column map
        [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
        [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
        ...
        ```

      而不是使用`CTable`模板类来声明表和表访问器类和 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 宏，以创建列映射，如本例所示：

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

   - 如果选择使用者**类型**的**命令**，则向导将使用`db_source`并`db_command`属性，并使用`db_column`创建列映射。 例如，它将创建此映射：

        ```cpp
        [db_source("<initialization_string>"), db_command("SQL_command")]
        ...
        // Column map using db_column is the same as for consumer type of 'table'
        ```

      而不是使用的命令和命令访问器在类声明命令类的.h 文件，例如：

        ```cpp
        // Command accessor class:
            class CListOrdersAccessor;
        // Command class:
            class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
        // ...
        // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
        // for consumer type of 'table'
        ```

      请参阅[属性的基本结构](../../windows/basic-mechanics-of-attributes.md)有关详细信息。

- **Type**

   选择其中一个单选按钮以指定是否将使用者类派生自`CTable`或`CCommand`（默认值）。

   - **Table**

      如果你想要使用，请选择此选项`CTable`或`db_table`若要创建的表和表访问器类声明。

   - **命令**

      如果你想要使用，请选择此选项`CCommand`或`db_command`创建命令和命令访问器类声明。 这是默认选择。

- **支持**

   选中复选框以指定的更新，在使用者 （默认值为 none） 中支持的种类。 以下各项将设置[DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892)和的相应条目[DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676)在属性集映射。

   - **更改**

      指定使用者在行集中支持的行数据的更新。

   - **插入**

      指定使用者支持到行集中插入行。

   - **删除**

      指定使用者支持的从行集中的行的删除。

## <a name="see-also"></a>请参阅

[ATL OLE DB 使用者](../../atl/reference/adding-an-atl-ole-db-consumer.md)<br/>
[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[连接字符串和数据链接 (OLE DB)](/previous-versions/windows/desktop/ms718376)
