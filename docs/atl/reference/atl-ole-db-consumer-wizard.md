---
title: "ATL OLE DB 使用者向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 6e35ce9038a8fd8f7aeeb00139511a8f45c1257d
ms.lasthandoff: 02/24/2017

---
# <a name="atl-ole-db-consumer-wizard"></a>ATL OLE DB 使用者向导
此向导设置 OLE DB 使用者类使用数据绑定到指定的 OLE DB 访问接口访问指定的数据源所需。  
  
> [!NOTE]
>  此向导要求您单击**数据源**按钮以选择数据源中输入名称之前`Class`和**.h 文件**字段。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **数据源**  
 **数据源**按钮使您可以设置使用指定的 OLE DB 访问接口的指定的数据源。 当您单击此按钮时**数据链接属性**对话框随即出现。 有关详细信息生成连接字符串和**数据链接属性**对话框中，请参阅[数据链接 API 概述](https://msdn.microsoft.com/library/ms718102.aspx)中[!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)]文档。  
  
> [!NOTE]
>  在早期版本中，按住 Shift 单击**数据源**按钮打开文件打开对话框，从中，您可以选择数据链接 (.udl) 文件。 不再支持此功能。  
  
 该对话框具有四个选项卡︰  
  
- **提供程序**选项卡  
  
- **连接**选项卡  
  
- **高级**选项卡  
  
- **所有**选项卡  
  
     以下附加信息描述中的选项卡**数据链接属性**对话框。  
  
     单击**确定**来完成。 **选择数据库对象**对话框随即出现。 从该对话框中，选择表、 视图或使用者将使用的存储的过程。  
  
 **提供程序**  
     选择相应的提供程序来管理与数据源的连接。 提供程序的类型通常是通过连接到的数据库的类型确定的。 单击`Next`按钮或单击**连接**选项卡。  
  
 **连接**  
     此选项卡上的内容取决于您选定的提供程序。 虽然有多种类型的提供程序，但本部分介绍连接的两个最常见︰ SQL 和 ODBC 中的数据。 其他类型是类似的变体此处所述的字段。  
  
     对于 SQL 数据︰  
  
    1. **选择或输入服务器名称︰**单击要在网络上，显示所有已注册的数据服务器的下拉列表菜单，选择一个。  
  
    2. **输入信息以登录到服务器上︰**输入用户名和密码以登录到数据服务器上。  
  
    3. **选择在服务器上的数据库︰**单击要显示所有已注册的数据库数据服务器上的下拉列表菜单，选择一个。  
  
         - 或 -  
  
 **附加数据库文件作为数据库名称︰**指定要用作数据库的文件; 输入显式路径名。  
  
        > [!NOTE]
        >  There is a security problem with the "Allow saving of password" feature of the Data Link Properties dialog box. In "Enter information to log on to the server," there are two radio buttons:  
  
 **使用 Windows NT 集成安全性**  
  
 **使用指定的用户名和密码**  
  
         If you select **Use a specific user name and password**, you have the option of saving the password (using the check box for "Allow saving password"); however, this option is not secure. It is recommended that you select **Use Windows NT integrated security**; this option is secure because it encrypts the password.  
  
         There might be situations in which you want to select "Allow saving password." For example, if you are releasing a library with a private database solution, you should not access the database directly but instead use a middle-tier application to verify the user (through whatever authentication scheme you choose) and then limit the sort of data available to the user.  
  
         For ODBC data:  
  
         1. **Specify the source of data:** You can use a data source name or a connection string.  
  
 **使用数据源名称︰**此下拉列表将显示在您计算机上注册的数据源。 您可以设置事先使用 ODBC 数据源管理器数据源-或-**使用连接字符串︰**可以输入连接字符串已获取，或者单击**生成**按钮;**选择数据源**对话框随即出现。 选择文件或计算机的数据源，然后单击**确定**。  
  
        > [!NOTE]
        >  You can obtain a connection string by viewing the properties of an existing connection in Server Explorer, or you can create a connection by double-clicking **Add Connection** in Server Explorer.  
  
         2. **Enter information to log on to the server:** Enter a user name and password to log on to the data server.  
  
         3. Enter the initial catalog to use.  
  
         4. Click **Test Connection**; if the test succeeds, click **OK**. If not, check your logon information, try another database, or try another data server.  
  
 **高级**  
 **网络设置︰**指定**模拟级别**（的服务器可以模拟客户端时使用; 直接对应于 RPC 模拟级别的模拟级别） 和**保护级别**（客户端和服务器之间发送的数据的保护级别直接对应于 RPC 保护级别）。  
  
 **其他︰**中**连接超时**，指定允许发生超时之前的空闲时间的秒数。 在**访问权限，**，在数据连接上指定的访问权限。  
  
     有关高级的初始化属性的详细信息，请参阅随每个特定的 OLE DB 访问接口提供的文档。  
  
 **All**  
     此选项卡上显示的数据源和您指定的连接的初始化属性的摘要。 您可以编辑这些值。  
  
     单击**确定**来完成。 **选择数据库对象**对话框随即出现。 从该对话框中，选择表、 视图或使用者将使用的存储的过程。  
  
 `Class`  
 选择数据源后，使用基于的表或您选择的存储的过程的默认类名称填充此框 (请参阅**选择数据源**下面)。 您可以编辑的类名。  
  
 **.h 文件**  
 选择数据源后，使用基于的表或您选择的存储的过程的默认标头类名称填充此框 (请参阅**选择数据源**下面)。 您可以编辑标头文件的名称，或选择现有的头文件。  
  
 **特性化**  
 此选项指定向导是否将创建使用者使用特性还是模板声明的类。 当选择此选项时，向导将使用属性而不是模板声明 （这是默认选项）。 当取消选择此选项时，向导将使用模板声明而不是属性。  
  
-   如果选择使用者**类型**的表，则向导将使用`db_source`和**db_table**属性来创建表和表访问器类声明中，并使用**db_column**来创建列映射，例如︰  
  
 ``` 
 // Inject table class and table accessor class declarations  
 [db_source("<initialization_string>"), db_table("dbo.Orders")]  
 ... 
 // Column map  
 [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;  
 [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];  
 ...  
 ```  
  
     而不是使用`CTable`模板类声明表和表访问器类和 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 宏来创建列映射，例如︰  
  
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
  
-   如果选择使用者**类型**的命令，则向导将使用`db_source`和**db_command**属性，并使用**db_column**来创建列映射，例如︰  
  
 ```  
 [db_source("<initialization_string>"), db_command("SQL_command")]  
 ... 
 // Column map using db_column is the same as for consumer type of 'table'  
 ```  
  
     而不是使用命令和命令访问器在类声明命令类的.h 文件中，例如︰  
  
 ```  
    Command accessor class:  
    class CListOrdersAccessor;  
    Command class:  
    class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;  
 ... 
 // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
 // for consumer type of 'table'  
 ```  
  
 请参阅[属性的基本结构](../../windows/basic-mechanics-of-attributes.md)有关详细信息。  
  
 **类型**  
 选择其中一个单选按钮来指定是否将使用者类派生自`CTable`或`CCommand`（默认值）。  
  
 **表**  
 选择此选项，如果您想要使用`CTable`或**db_table**创建表和表访问器类声明。  
  
 **命令**  
 选择此选项，如果您想要使用`CCommand`或**db_command**创建命令和命令访问器类声明。 这是默认选择。  
  
 **支持**  
 选中复选框可指定要在使用者 （默认值为 none） 中支持的更新类型。 以下各项将设置[DBPROP_IRowsetChange](https://msdn.microsoft.com/library/ms715892.aspx)和的相应条目中[DBPROP_UPDATABILITY](https://msdn.microsoft.com/library/ms722676.aspx)在属性集中的映射。  
  
 **更改**  
 指定使用者在行集中支持更新的行数据。  
  
 **插入**  
 指定使用者支持的行插入到行集中。  
  
 **删除**  
 指定使用者支持删除从行集中的行。  
  
## <a name="see-also"></a>另请参阅  
 [ATL OLE DB 使用者](../../atl/reference/adding-an-atl-ole-db-consumer.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [连接字符串和数据链接 (OLE DB)](https://msdn.microsoft.com/library/ms718376.aspx)

