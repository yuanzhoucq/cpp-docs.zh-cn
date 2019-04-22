---
title: 数据源：管理连接 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], multiuser environments
- generalizing connection strings
- ODBC [C++], disconnecting from data sources
- connection strings [C++], generalizing
- database connections [C++], creating
- GetDefaultConnect method
- connections [C++], data source
- ODBC connections [C++], configuring
- disconnecting from data sources
- databases [C++], connecting to
- ODBC connections [C++], disconnecting
- data sources [C++], connecting to
- ODBC connections [C++], connecting to data source
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: c0adbcdd-c000-40c6-b199-09ffdc7b6ef2
ms.openlocfilehash: 5b646ca0eb86d3addabaad59ca23f56cfe914114
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041158"
---
# <a name="data-source-managing-connections-odbc"></a>数据源：管理连接 (ODBC)

本主题适用于 MFC ODBC 类。

本主题说明：

- [如何配置数据源](#_core_configuring_a_data_source)。

- [多用户环境如何影响数据源和及其记录集](#_core_working_in_a_multiuser_environment)。

- [为什么通用化到数据源的连接字符串](#_core_generalizing_the_connection_string)。

- [如何连接到数据源](#_core_connecting_to_a_specific_data_source)。

- [如何从数据源断开连接](#_core_disconnecting_from_a_data_source)。

- [如何重用 CDatabase 对象](#_core_reusing_a_cdatabase_object)。

连接到数据源意味着建立与 DBMS 就能访问的数据之间的通信。 当从应用程序通过 ODBC 驱动程序连接到数据源时，驱动程序将连接，本地或网络中。

您可以连接到对其具有 ODBC 驱动程序的任何数据源。 应用程序的用户还必须具有相同的 ODBC 驱动程序用于数据源。 有关重新分发 ODBC 驱动程序的详细信息，请参阅[为客户重新分发 ODBC 组件](../../data/odbc/redistributing-odbc-components-to-your-customers.md)。

##  <a name="_core_configuring_a_data_source"></a> 配置数据源

ODBC 管理器用于配置你的数据源。 您可以在安装后使用 ODBC 管理器添加或删除数据源。 在创建应用程序时，您可以将用户引导到 ODBC 管理器以让他们添加数据源，或可以通过直接调用 ODBC 安装到你的应用程序中构建此功能。 有关详细信息，请参阅[ODBC 管理器](../../data/odbc/odbc-administrator.md)。

您可以使用 Excel 文件作为数据源，并且需要配置文件，使之注册并将出现在**选择数据源**对话框。

#### <a name="to-use-an-excel-file-as-a-data-source"></a>若要使用的 Excel 文件作为数据源

1. 使用 ODBC 数据源管理器配置文件。

1. 上**文件 DSN**选项卡上，单击**添加**。

1. 在中**创建新的数据源**对话框中，选择一个 Excel 驱动程序，并单击**下一步**。

1. 单击**浏览**，并选择要用作数据源的文件的名称。

> [!NOTE]
>  可能需要选择**的所有文件**下拉菜单以查看.xls 文件中。

1. 单击“下一步” ，再单击“完成” 。

1. 在中**ODBC Microsoft Excel 安装程序**对话框框中，选择数据库版本和工作簿。

##  <a name="_core_working_in_a_multiuser_environment"></a> 在多用户环境中工作

如果多个用户连接到数据源，他们可以更改数据，而您在记录集中操作。 同样，所做的更改可能会影响其他用户的记录集。 有关详细信息，请参阅[记录集：如何记录集更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)并[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。

##  <a name="_core_generalizing_the_connection_string"></a> 将连接字符串通用化

向导使用默认连接字符串建立与数据源的连接。 此连接用于在开发应用程序时查看表和列。 但是，此默认连接字符串可能不是适用于你的用户连接到数据源通过您的应用程序。 例如，其数据源以及指向其位置的路径可能不同于在开发应用程序时使用。 在这种情况下，应重新实现[crecordset:: Getdefaultconnect](../../mfc/reference/crecordset-class.md#getdefaultconnect)成员函数以更通用的方式，并放弃该向导实现。 例如，使用以下方法之一：

- 注册和管理使用 ODBC 管理器的连接字符串。

- 编辑连接字符串并删除数据源名称。 该框架提供 ODBC 作为数据源;在运行时，ODBC 将显示对话框，询问有关数据源名称和其他任何所需的连接信息。

- 提供数据源名称。 ODBC 将要求提供用户 ID 和密码，如果所需。 例如，再通用化，连接字符串如下所示：

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   此连接字符串指定可信的连接，它使用 Windows NT 集成安全性。 应该避免将密码进行硬编码或者指定空白密码，因为执行此操作会创建严重的安全漏洞。 相反，您可以为`GetDefaultConnect`新的连接字符串，以便它将查询的用户 ID 和密码。

    ```cpp
    // User must select data source and supply user ID and password:
        return "ODBC;";
    // User ID and password required:
        return "ODBC;DSN=mydb;";
    // Password required (myuserid must be replaced with a valid user ID):
        return "ODBC;DSN=mydb;UID=myuserid;";
    // Hard-coded user ID and password (SECURITY WEAKNESS--AVOID):
        return "ODBC;DSN=mydb;UID=sa;PWD=777;";
    ```

##  <a name="_core_connecting_to_a_specific_data_source"></a> 连接到特定的数据源

若要连接到特定的数据源，您的数据源必须已进行了配置与[ODBC 管理器](../../data/odbc/odbc-administrator.md)。

#### <a name="to-connect-to-a-specific-data-source"></a>若要连接到特定的数据源

1. 构造`CDatabase`对象。

1. 调用其`OpenEx`或`Open`成员函数。

有关如何指定数据源不是指定了一个向导执行的任务的详细信息，请参阅[不同](../../mfc/reference/cdatabase-class.md#openex)或[CDatabase::Open](../../mfc/reference/cdatabase-class.md#open)中*MFC引用*。

##  <a name="_core_disconnecting_from_a_data_source"></a> 与数据源断开连接

您必须关闭任何打开的记录集之前调用`Close`成员函数的`CDatabase`。 在关联的记录集中`CDatabase`对象则需要关闭任何挂起`AddNew`或`Edit`语句被取消并且所有挂起的事务将回滚。

#### <a name="to-disconnect-from-a-data-source"></a>若要从数据源断开连接

1. 调用`CDatabase`对象的[关闭](../../mfc/reference/cdatabase-class.md#close)成员函数。

1. 销毁对象，除非你想要重复使用它。

##  <a name="_core_reusing_a_cdatabase_object"></a> 重用 CDatabase 对象

可以重复使用`CDatabase`后断开连接，无论是使用可以重新连接到同一数据源，还是连接到不同的数据源的对象。

#### <a name="to-reuse-a-cdatabase-object"></a>重用 CDatabase 对象

1. 关闭对象的原始连接。

1. 而不是销毁的对象，调用其`OpenEx`或`Open`再次成员函数。

## <a name="see-also"></a>请参阅

[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[数据源：确定数据源 (ODBC) 的架构](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)