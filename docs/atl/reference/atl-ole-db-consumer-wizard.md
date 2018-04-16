---
title: ATL OLE DB 使用者向导 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.consumer.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- connection strings [C++], OLE DB consumers
- ATL OLE DB Consumer Wizard
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d12020b6adfca2c23dc610b5e596ff883bb9e7ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="atl-ole-db-consumer-wizard"></a>ATL OLE DB 使用者向导
此向导安装 OLE DB 使用者类，该类数据绑定通过指定的 OLE DB 访问接口访问指定的数据源所需。  
  
> [!NOTE]
>  此向导要求您单击**数据源**按钮以选择数据源中输入名称之前`Class`和**.h 文件**字段。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **数据源**  
 **数据源**按钮的使你可以设置指定的数据源使用指定的 OLE DB 提供程序。 单击此按钮时**数据链接属性**对话框随即出现。 有关生成连接字符串的详细信息和**数据链接属性**对话框中，请参阅[数据链接 API 概述](https://msdn.microsoft.com/library/ms718102.aspx)Windows SDK 文档中。  
  
> [!NOTE]
>  在以前版本中，Shift 单击**数据源**按钮打开文件打开对话框，从中可以选择数据链接 (.udl) 文件。 不再支持此功能。  
  
 对话框中有四个选项卡：  
  
- **提供程序**选项卡  
  
- **连接**选项卡  
  
- **高级**选项卡  
  
- **所有**选项卡  
  
     下面的其他信息介绍中的选项卡**数据链接属性**对话框。  
  
     单击**确定**完成。 **选择数据库对象**对话框随即出现。 从该对话框中，选择表、 视图或使用者将使用的存储的过程。  
  
 **提供程序**  
     选择适当的提供程序来管理与数据源的连接。 提供程序的类型通常是通过连接到的数据库的类型确定的。 单击`Next`按钮或单击**连接**选项卡。  
  
 **连接**  
     此选项卡的内容取决于你选择的提供程序。 尽管有许多类型的提供程序，本部分介绍了连接的两个最常见： SQL 和 ODBC 的数据。 其他类型是类似的变体此处描述的字段。  
  
     对于 SQL 数据：  
  
    1. **选择或输入服务器名称：**单击要在网络上，显示所有已注册的数据服务器的下拉列表菜单，然后选择一个。  
  
    2. **输入信息以登录到服务器：**输入用户名和密码以登录到数据服务器。  
  
    3. **选择服务器上的数据库：**单击要在数据服务器上，显示所有已注册的数据库的下拉列表菜单，然后选择一个。  
  
         或  
  
 **将作为数据库名称的数据库文件附加：**指定要用作数据库的文件; 输入显式路径名。  
  
        > [!NOTE]
        >  There is a security problem with the "Allow saving of password" feature of the Data Link Properties dialog box. In "Enter information to log on to the server," there are two radio buttons:  
  
 **使用 Windows NT 集成安全性**  
  
 **使用特定用户名和密码**  
  
         If you select **Use a specific user name and password**, you have the option of saving the password (using the check box for "Allow saving password"); however, this option is not secure. It is recommended that you select **Use Windows NT integrated security**; this option is secure because it encrypts the password.  
  
         There might be situations in which you want to select "Allow saving password." For example, if you are releasing a library with a private database solution, you should not access the database directly but instead use a middle-tier application to verify the user (through whatever authentication scheme you choose) and then limit the sort of data available to the user.  
  
         For ODBC data:  
  
         1. **Specify the source of data:** You can use a data source name or a connection string.  
  
 **使用数据源名称：**此下拉列表显示在您的计算机中注册的数据源。 你可以设置提前使用 ODBC 数据源管理器数据源-或-**使用连接字符串：**输入连接字符串已获取，或单击**生成**按钮;**选择数据源**对话框随即出现。 选择文件或计算机的数据源，然后单击**确定**。  
  
        > [!NOTE]
        >  You can obtain a connection string by viewing the properties of an existing connection in Server Explorer, or you can create a connection by double-clicking **Add Connection** in Server Explorer.  
  
         2. **Enter information to log on to the server:** Enter a user name and password to log on to the data server.  
  
         3. Enter the initial catalog to use.  
  
         4. Click **Test Connection**; if the test succeeds, click **OK**. If not, check your logon information, try another database, or try another data server.  
  
 **高级**  
 **网络设置：**指定**模拟级别**（的服务器可以使用模拟客户端时; 直接对应于 RPC 模拟级别的模拟级别） 和**保护级别**（客户端和服务器之间发送的数据的保护级别对应直接到 RPC 保护级别）。  
  
 **其他：**中**连接超时**，指定允许发生超时之前的空闲时间的秒数。 在**访问权限**，指定有关数据连接的访问权限。  
  
     有关高级的初始化属性的详细信息，请参阅随每个特定的 OLE DB 提供程序提供的文档。  
  
 **All**  
     此选项卡显示的数据源和具有指定的连接的初始化属性的摘要。 你可以编辑这些值。  
  
     单击**确定**完成。 **选择数据库对象**对话框随即出现。 从该对话框中，选择表、 视图或使用者将使用的存储的过程。  
  
 `Class`  
 选择数据源后，使用基于的表或你选择的存储的过程的默认类名称填充此框 (请参阅**选择数据源**下面)。 你可以编辑的类名称。  
  
 **.h 文件**  
 选择数据源后，使用基于的表或你选择的存储的过程的默认标头类名称填充此框 (请参阅**选择数据源**下面)。 你可以编辑标头文件的名称，或选择一个现有的标头文件。  
  
 **特性化**  
 此选项指定向导是否将创建使用者使用属性或模板声明的类。 当选择此选项时，向导将使用而不是模板声明 （这是默认选项） 的属性。 当你取消选择此选项时，向导而不是特性使用模板声明。  
  
-   如果选择使用者**类型**的表，则向导将使用`db_source`和**db_table**属性创建的表和表访问器类声明，并使用**db_column**来创建列映射中，例如：  
  
 ``` 
 // Inject table class and table accessor class declarations  
 [db_source("<initialization_string>"), db_table("dbo.Orders")]  
 ... 
 // Column map  
 [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;  
 [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];  
 ...  
 ```  
  
     而不是使用`CTable`模板类来声明表和表访问器类和 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 宏，来创建列映射中，例如：  
  
 ``` 
 // Table accessor class  
    class COrdersAccessor; *// Table class  
    class COrders : public CTable<CAccessor<COrdersAccessor>>;  
 ... 
 // Column map  
    BEGIN_COLUMN_MAP(COrderDetailsAccessor) 
    COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)  
    COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)  
 ...  
    END_COLUMN_MAP() 
 ```  
  
-   如果选择使用者**类型**的命令，该向导使用`db_source`和**db_command**属性，并使用**db_column**来创建列映射中，例如:  
  
 ```  
 [db_source("<initialization_string>"), db_command("SQL_command")]  
 ... 
 // Column map using db_column is the same as for consumer type of 'table'  
 ```  
  
     而不是使用的命令和命令访问器类声明命令类的.h 文件中，例如：  
  
 ```  
    Command accessor class:  
    class CListOrdersAccessor;  
    Command class:  
    class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;  
 ... 
 // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
 // for consumer type of 'table'  
 ```  
  
 请参阅[特性的基本机制](../../windows/basic-mechanics-of-attributes.md)有关详细信息。  
  
 **Type**  
 选择一个指定是否将使用者类派生自这些单选按钮`CTable`或`CCommand`（默认值）。  
  
 **Table**  
 选择此选项，如果你想要使用`CTable`或**db_table**若要创建的表和表访问器类声明。  
  
 **命令**  
 选择此选项，如果你想要使用`CCommand`或**db_command**创建命令和命令访问器类声明。 这是默认选项。  
  
 **支持**  
 选择复选框来指定要在使用者 （默认值为 none） 中受支持的更新类型。 以下各项将设置[DBPROP_IRowsetChange](https://msdn.microsoft.com/library/ms715892.aspx)和的相应条目[DBPROP_UPDATABILITY](https://msdn.microsoft.com/library/ms722676.aspx)属性中设置映射。  
  
 **更改**  
 指定使用者，支持在行集中的行数据的更新。  
  
 插入  
 指定使用者支持到行集中插入行。  
  
 **删除**  
 指定使用者，支持删除从行集中的行。  
  
## <a name="see-also"></a>请参阅  
 [ATL OLE DB 使用者](../../atl/reference/adding-an-atl-ole-db-consumer.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [连接字符串和数据链接 (OLE DB)](https://msdn.microsoft.com/library/ms718376.aspx)
