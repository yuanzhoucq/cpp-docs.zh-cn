---
title: "数据源：管理连接 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "连接字符串 [C++], 一般化"
  - "连接 [C++], 数据源"
  - "数据源 [C++], 连接"
  - "数据库连接 [C++], 创建"
  - "数据库连接 [C++], MFC ODBC 类"
  - "数据库 [C++], 连接"
  - "与数据源断开连接"
  - "一般化连接字符串"
  - "GetDefaultConnect 方法"
  - "ODBC [C++], 与数据源断开连接"
  - "ODBC 连接 [C++], 配置"
  - "ODBC 连接 [C++], 连接到数据源"
  - "ODBC 连接 [C++], 断开连接"
  - "ODBC 数据源 [C++], 连接"
  - "ODBC 数据源 [C++], 多用户环境"
ms.assetid: c0adbcdd-c000-40c6-b199-09ffdc7b6ef2
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数据源：管理连接 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 本主题说明：  
  
-   [如何配置数据源](#_core_configuring_a_data_source)。  
  
-   [多用户环境如何影响数据源及其记录集](#_core_working_in_a_multiuser_environment)。  
  
-   [为什么通用化到数据源的连接字符串](#_core_generalizing_the_connection_string)。  
  
-   [如何连接数据源](#_core_connecting_to_a_specific_data_source)。  
  
-   [如何断开与数据源的连接](#_core_disconnecting_from_a_data_source)。  
  
-   [重用 CDatabase 对象的方式](#_core_reusing_a_cdatabase_object)。  
  
 连接到数据源意味着与 DBMS 建立通信以访问数据。  当您通过 ODBC 驱动程序从应用程序连接到一个数据源时，驱动程序将为您建立本地连接或网络连接。  
  
 可以连接到具有其 ODBC 驱动程序的任何数据源。  您的应用程序的用户也必须具有同样的用于数据源的 ODBC 驱动程序。  有关再发行 ODBC 驱动程序的更多信息，请参见[为客户重新分布 ODBC 组件](../../data/odbc/redistributing-odbc-components-to-your-customers.md)。  
  
##  <a name="_core_configuring_a_data_source"></a> 配置数据源  
 ODBC 管理器用于配置您的数据源。  也可在安装完成后使用 ODBC 管理器添加或移除数据源。  创建应用程序时，可以将用户引导到 ODBC 管理器以让他们添加数据源，或者直接调用 ODBC 安装，将此项功能内置到应用程序中。  有关更多信息，请参见 [ODBC 管理器](../../data/odbc/odbc-administrator.md)。  
  
 也可以用 Excel 文件作为数据源，并且需要配置该文件使之注册并显示在“选择数据源”对话框中。  
  
#### 使用 Excel 文件作为数据源  
  
1.  使用 ODBC 数据源管理器配置文件。  
  
2.  在“文件 DSN”选项卡上单击“添加”。  
  
3.  在**“创建新数据源”**对话框中，选择一个 Excel 驱动程序，再单击**“下一步”**。  
  
4.  单击“浏览”，然后选择要用作数据源的文件名。  
  
> [!NOTE]
>  您可能需要在下拉菜单中选择**“所有文件”**以查看 .xls 文件。  
  
1.  单击**“下一步”**，然后单击**“完成”**。  
  
2.  在“ODBC Microsoft Excel 安装”对话框中，选择数据库版本和工作簿。  
  
##  <a name="_core_working_in_a_multiuser_environment"></a> 在多用户环境下工作  
 如果有多个用户连接到了数据源，您在记录集中操作数据源的同时，这些用户可以更改数据。  同样，您所做的更改可能会影响其他用户的记录集。  有关更多信息，请参见[记录集：记录集如何更新记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) 和 [事务 \(ODBC\)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="_core_generalizing_the_connection_string"></a> 将连接字符串通用化  
 该向导用默认连接字符串建立到数据源的连接。  在开发应用程序时，可使用该连接查看表和列。  但是，该默认连接字符串可能并不适合用户通过您的应用程序连接到数据源。  例如，用户的数据源和数据源位置路径可能与您在开发应用程序时使用的数据源及路径不同。  这种情况下，应该以更一般的方式重新执行 [CRecordset::GetDefaultConnect](../Topic/CRecordset::GetDefaultConnect.md) 成员函数，并且放弃该向导实现。  例如，用下列方法之一：  
  
-   使用 ODBC 管理器注册和管理连接字符串。  
  
-   编辑连接字符串并移除数据源名称。  框架提供 ODBC 作为数据源；在运行时，ODBC 将显示一个对话框，要求提供数据源名称和其他任何所需的连接信息。  
  
-   只提供数据源名称。  如果需要，ODBC 将要求提供用户 ID 和密码。  例如，在进行通用化处理之前，连接字符串是这样的：  
  
    ```  
    CString CApp1Set::GetDefaultConnect()  
    {  
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";  
    }  
    ```  
  
     此连接字符串指定可信连接，它使用 Windows NT 集成安全性。  您应该避免将密码硬编码或者指定空白密码，否则会导致严重的安全漏洞。  您可以为 `GetDefaultConnect` 提供新的连接字符串，使其查询用户 ID 和密码。  
  
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
  
##  <a name="_core_connecting_to_a_specific_data_source"></a> 连接到特定的数据源  
 若要连接到特定的数据源，必须已使用 [ODBC 管理器](../../data/odbc/odbc-administrator.md)对您的数据源进行了配置。  
  
#### 连接到特定的数据源  
  
1.  构造 `CDatabase` 对象。  
  
2.  调用它的 `OpenEx` 或 **Open** 成员函数。  
  
 对于数据源不同于使用向导所指定的数据源的情况，有关如何指定该数据源的更多信息，请参见“MFC 参考”中的 [CDatabase::OpenEx](../Topic/CDatabase::OpenEx.md) 或 [CDatabase::Open](../Topic/CDatabase::Open.md)。  
  
##  <a name="_core_disconnecting_from_a_data_source"></a> 从数据源断开连接  
 调用 `CDatabase` 的 **Close** 成员函数前，必须关闭所有打开的记录集。  在与要关闭的 `CDatabase` 对象关联的记录集中，将取消任何挂起的 `AddNew` 或 **Edit** 语句，并且回滚所有挂起的事务。  
  
#### 从数据源断开连接  
  
1.  调用 `CDatabase` 对象的 [Close](../Topic/CDatabase::Close.md) 成员函数。  
  
2.  销毁该对象，除非您要重用它。  
  
##  <a name="_core_reusing_a_cdatabase_object"></a> 重用 CDatabase 对象  
 从 `CDatabase` 对象断开连接后可以重用它，既可以用它重新连接到同一个数据源，也可用它连接到不同的数据源。  
  
#### 重用 CDatabase 对象  
  
1.  关闭该对象的原始连接。  
  
2.  再次调用该对象的 `OpenEx` 或 **Open** 成员函数，而不是销毁它。  
  
## 请参阅  
 [数据源 \(ODBC\)](../../data/odbc/data-source-odbc.md)   
 [数据源：确定数据源的架构 \(ODBC\)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)