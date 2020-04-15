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
ms.openlocfilehash: 107a5e20b70f67be74b6e6f861bd539446e9d4ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374532"
---
# <a name="data-source-managing-connections-odbc"></a>数据源：管理连接 (ODBC)

本主题适用于 MFC ODBC 类。

本主题介绍：

- [如何配置数据源](#_core_configuring_a_data_source)。

- [多用户环境如何影响数据源及其记录集](#_core_working_in_a_multiuser_environment)。

- [为什么将连接字符串概括为数据源](#_core_generalizing_the_connection_string)。

- [如何连接到数据源](#_core_connecting_to_a_specific_data_source)。

- [如何断开与数据源的连接](#_core_disconnecting_from_a_data_source)。

- [如何重用 CDatabase 对象](#_core_reusing_a_cdatabase_object)。

连接到数据源意味着与 DBMS 建立通信以访问数据。 当您通过 ODBC 驱动程序从应用程序连接到数据源时，驱动程序会在本地或网络中为您建立连接。

您可以连接到具有 ODBC 驱动程序的任何数据源。 应用程序的用户还必须为其数据源使用相同的 ODBC 驱动程序。 有关重新分发 ODBC 驱动程序的详细信息，请参阅[将 ODBC 组件重新分发给您的客户](../../data/odbc/redistributing-odbc-components-to-your-customers.md)。

## <a name="configuring-a-data-source"></a><a name="_core_configuring_a_data_source"></a>配置数据源

ODBC 管理员用于配置数据源。 您还可以在安装后使用 ODBC 管理员添加或删除数据源。 创建应用程序时，可以将用户定向到 ODBC 管理员，让他们添加数据源，也可以通过直接进行 ODBC 安装调用将此功能构建到应用程序中。 有关详细信息，请参阅[ODBC 管理员](../../data/odbc/odbc-administrator.md)。

您可以将 Excel 文件用作数据源，并且需要配置该文件，以便该文件被注册并显示在 **"选择数据源**"对话框中。

#### <a name="to-use-an-excel-file-as-a-data-source"></a>将 Excel 文件用作数据源

1. 使用 ODBC 数据源管理员配置文件。

1. 在 **"文件 DSN"** 选项卡上，单击"**添加**"。

1. 在 **"创建新数据源"** 对话框中，选择 Excel 驱动程序，然后单击"**下一步**"。

1. 单击 **"浏览**"并选择要用作日期源的文件的名称。

> [!NOTE]
> 您可能需要选择下拉菜单中的所有**文件**才能查看 .xls 文件。

1. 单击“下一步”****，然后单击“完成”****。

1. 在**ODBC 微软 Excel 设置**对话框中，选择数据库版本和工作簿。

## <a name="working-in-a-multiuser-environment"></a><a name="_core_working_in_a_multiuser_environment"></a>在多用户环境中工作

如果多个用户连接到数据源，则可以在记录集中操作数据时更改数据。 同样，您的更改可能会影响其他用户的记录集。 有关详细信息，请参阅[记录集：记录集如何更新记录 （ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)和[事务 （ODBC）。](../../data/odbc/transaction-odbc.md)

## <a name="generalizing-the-connection-string"></a><a name="_core_generalizing_the_connection_string"></a>概括连接字符串

向导使用默认连接字符串建立与数据源的连接。 在开发应用程序时，使用此连接可以查看表和列。 但是，此默认连接字符串可能不适合用户通过应用程序连接到数据源。 例如，它们的数据源及其位置的路径可能与开发应用程序时所使用的路径不同。 在这种情况下，您应该以更通用的方式重新实现[CRecordset：：getDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect)成员函数，并放弃向导实现。 例如，使用以下方法之一：

- 使用 ODBC 管理员注册和管理连接字符串。

- 编辑连接字符串并删除数据源名称。 该框架提供ODBC作为数据源;在运行时，ODBC 将显示一个对话框，询问数据源名称和任何其他必需的连接信息。

- 仅提供数据源名称。 如果需要，ODBC 会询问用户 ID 和密码。 例如，在概括之前，连接字符串如下所示：

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   此连接字符串指定使用 Windows NT 集成安全性的受信任连接。 应避免对密码进行硬编码或指定空白密码，因为这样做会产生重大的安全缺陷。 相反，您可以提供新的`GetDefaultConnect`连接字符串，以便它查询用户 ID 和密码。

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

## <a name="connecting-to-a-specific-data-source"></a><a name="_core_connecting_to_a_specific_data_source"></a>连接到特定数据源

要连接到特定数据源，数据源必须已配置了[ODBC 管理员](../../data/odbc/odbc-administrator.md)。

#### <a name="to-connect-to-a-specific-data-source"></a>连接到特定数据源

1. 构造`CDatabase`对象。

1. 调用其`OpenEx`或`Open`成员函数。

有关如何指定数据源（如果数据源是使用向导指定的数据源以外的数据源）的详细信息，请参阅[CDatabase：：OpenEx](../../mfc/reference/cdatabase-class.md#openex)或[CDatabase：：](../../mfc/reference/cdatabase-class.md#open)在*MFC 参考*中打开。

## <a name="disconnecting-from-a-data-source"></a><a name="_core_disconnecting_from_a_data_source"></a>与数据源断开连接

在调用 的成员函数之前，`Close`必须关闭任何打开的记录`CDatabase`集。 在与要关闭`CDatabase`的对象关联的记录集中，将取消任何挂起`AddNew`或`Edit`语句，并回滚所有挂起的事务。

#### <a name="to-disconnect-from-a-data-source"></a>与数据源断开连接

1. 调用`CDatabase`对象的[关闭](../../mfc/reference/cdatabase-class.md#close)成员函数。

1. 销毁对象，除非您要重用它。

## <a name="reusing-a-cdatabase-object"></a><a name="_core_reusing_a_cdatabase_object"></a>重用 C 数据库对象

在断开`CDatabase`对象断开后，可以重用该对象，无论是使用它重新连接到同一数据源还是连接到其他数据源。

#### <a name="to-reuse-a-cdatabase-object"></a>重用 CDatabase 对象

1. 关闭对象的原始连接。

1. 不要破坏对象，而是再次调用其`OpenEx`或`Open`成员函数。

## <a name="see-also"></a>另请参阅

[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[数据源：确定数据源的架构 (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)
