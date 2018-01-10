---
title: "数据源： 管理连接 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9b83093496d355fdba8b5d714875d08040ae28ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="data-source-managing-connections-odbc"></a>数据源：管理连接 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 本主题说明：  
  
-   [如何配置数据源](#_core_configuring_a_data_source)。  
  
-   [多用户环境中如何影响数据源和其记录集](#_core_working_in_a_multiuser_environment)。  
  
-   [为什么通用化数据源的连接字符串](#_core_generalizing_the_connection_string)。  
  
-   [如何连接到数据源](#_core_connecting_to_a_specific_data_source)。  
  
-   [如何从数据源断开连接](#_core_disconnecting_from_a_data_source)。  
  
-   [如何 CDatabase 对象重用](#_core_reusing_a_cdatabase_object)。  
  
 连接到数据源，则意味着建立与 DBMS 就能访问的数据之间的通信。 当通过从应用程序的 ODBC 驱动程序连接到数据源时，本地或通过网络驱动程序，可以为你的连接。  
  
 你可以连接到您对其具有 ODBC 驱动程序的任何数据源。 应用程序的用户还必须为其数据源相同的 ODBC 驱动程序。 有关重新分发 ODBC 驱动程序的详细信息，请参阅[为客户重新分发 ODBC 组件](../../data/odbc/redistributing-odbc-components-to-your-customers.md)。  
  
##  <a name="_core_configuring_a_data_source"></a>配置数据源  
 ODBC 管理器用于配置您的数据源。 你可以在安装后使用 ODBC 管理器添加或删除数据源。 在创建应用程序时，你可以将用户引导到 ODBC 管理器以让他们添加数据源，或可以通过进行直接调用 ODBC 安装到你的应用程序中生成此功能。 有关详细信息，请参阅[ODBC 管理器](../../data/odbc/odbc-administrator.md)。  
  
 你可以使用 Excel 文件作为数据源，并且需要进行配置文件，以便已注册并将出现在**选择数据源**对话框。  
  
#### <a name="to-use-an-excel-file-as-a-data-source"></a>若要使用 Excel 文件作为数据源  
  
1.  使用 ODBC 数据源管理器配置文件。  
  
2.  上**文件 DSN**选项卡上，单击**添加**。  
  
3.  在**新建数据源**对话框中，选择 Excel 驱动程序，，然后单击**下一步**。  
  
4.  单击**浏览**，并选择要用作数据源的文件的名称。  
  
> [!NOTE]
>  你可能需要选择**所有文件**下拉菜单以查看.xls 文件中。  
  
1.  单击“下一步” ，再单击“完成” 。  
  
2.  在**ODBC Microsoft Excel 安装程序**对话框框中，选择的数据库版本和工作簿。  
  
##  <a name="_core_working_in_a_multiuser_environment"></a>在多用户环境中工作  
 如果多个用户连接到数据源，他们可以更改数据，而你记录集内操作。 同样，所做的更改可能会影响其他用户的记录集。 有关详细信息，请参阅[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)和[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="_core_generalizing_the_connection_string"></a>通用化的连接字符串  
 向导使用默认连接字符串来建立与数据源的连接。 使用此连接，在开发你的应用程序时查看表和列。 但是，此默认连接字符串不可能适用于通过应用程序数据源的用户的连接。 例如，其数据源和到其位置的路径可能不同于在开发应用程序中使用。 在这种情况下，应重新实现[CRecordset::GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect)成员函数中以更通用的方式，并放弃向导实现。 例如，使用以下方法之一：  
  
-   注册和管理使用 ODBC 管理器的连接字符串。  
  
-   编辑连接字符串并删除数据源名称。 框架提供了 ODBC 作为数据源;在运行时，ODBC 显示对话框，询问有关数据源名称和任何其他所需的连接信息。  
  
-   提供数据源名称。 ODBC，要求您的用户 ID 和密码，如果所需。 例如，在通用化之前, 的连接字符串如下所示：  
  
    ```  
    CString CApp1Set::GetDefaultConnect()  
    {  
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";  
    }  
    ```  
  
     此连接字符串指定可信的连接，它使用 Windows NT 集成安全性。 应避免将密码进行硬编码或指定一个空密码，因为这样创建主要的安全漏洞。 相反，你可以为提供`GetDefaultConnect`新的连接字符串，以便它会询问是否用户 ID 和密码。  
  
    ```  
    // User must select data source and supply user ID and password:  
        return "ODBC;";  
    // User ID and password required:  
        return "ODBC;DSN=mydb;";  
    // Password required (myuserid must be replaced with a valid user ID):  
        return "ODBC;DSN=mydb;UID=myuserid;";  
    // Hard-coded user ID and password (SECURITY WEAKNESS--AVOID):  
        return "ODBC;DSN=mydb;UID=sa;PWD=777;";  
    ```  
  
##  <a name="_core_connecting_to_a_specific_data_source"></a>连接到特定数据源  
 若要连接到特定数据源，您的数据源必须已进行了配置与[ODBC 管理器](../../data/odbc/odbc-administrator.md)。  
  
#### <a name="to-connect-to-a-specific-data-source"></a>若要连接到特定数据源  
  
1.  构造`CDatabase`对象。  
  
2.  调用其`OpenEx`或**打开**成员函数。  
  
 有关如何指定数据源，如果它是用向导指定之外的内容的详细信息，请参阅[CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex)或[CDatabase::Open](../../mfc/reference/cdatabase-class.md#open)中*MFC引用*。  
  
##  <a name="_core_disconnecting_from_a_data_source"></a>从数据源断开连接  
 您必须关闭任何打开的记录集之前调用**关闭**成员函数`CDatabase`。 与关联的记录集内`CDatabase`对象你想要关闭，任何挂起的`AddNew`或**编辑**语句被取消，并将所有挂起的事务将回滚。  
  
#### <a name="to-disconnect-from-a-data-source"></a>若要从数据源断开连接  
  
1.  调用`CDatabase`对象的[关闭](../../mfc/reference/cdatabase-class.md#close)成员函数。  
  
2.  除非你想要重用它，请销毁对象。  
  
##  <a name="_core_reusing_a_cdatabase_object"></a>重用 CDatabase 对象  
 你可以重复使用`CDatabase`后断开，无论是使用重新连接到同一数据源，还是连接到不同的数据源的对象。  
  
#### <a name="to-reuse-a-cdatabase-object"></a>若要重用 CDatabase 对象  
  
1.  关闭对象的原始连接。  
  
2.  而不是销毁对象，调用其`OpenEx`或**打开**再次成员函数。  
  
## <a name="see-also"></a>请参阅  
 [数据源 (ODBC)](../../data/odbc/data-source-odbc.md)   
 [数据源： 确定数据源 (ODBC) 的架构](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)   
 [CRecordset 类](../../mfc/reference/crecordset-class.md)