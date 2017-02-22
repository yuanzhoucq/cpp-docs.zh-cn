---
title: "ATL OLE DB 使用者向导 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.consumer.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL OLE DB 使用者向导"
  - "ATL 项目, 添加 ATL OLE DB 使用者"
  - "连接字符串 [C++], OLE DB 使用者"
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# ATL OLE DB 使用者向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此向导安装 OLE DB 使用者类，该类包含通过指定的 OLE DB 提供程序访问指定数据源所需的数据绑定。  
  
> [!NOTE]
>  此向导要求在 `Class` 和**“.h 文件”**字段中输入名称之前，单击**“数据源”**按钮选择数据源。  
  
## UIElement 列表  
 **数据源**  
 **“数据源”**按钮使您可以使用指定的 OLE DB 提供程序设置指定的数据源。  单击此按钮时，将出现**“数据链接属性”**对话框。  有关生成连接字符串和**“数据链接属性”**对话框的更多信息，请参见 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 文档中的[数据链接 API 概述](https://msdn.microsoft.com/en-us/library/ms718102.aspx)。  
  
> [!NOTE]
>  在以前的版本中，按住 Shift 单击**“数据源”**按钮将打开“文件打开”对话框，从中可以选择数据链接 \(.udl\) 文件。  不再支持该功能。  
  
 此对话框有四个选项卡：  
  
-   **“提供程序”**选项卡  
  
-   **“连接”**选项卡  
  
-   **“高级”**选项卡  
  
-   **“全部”**选项卡  
  
     以下附加信息描述了**“数据链接属性”**对话框中的选项卡。  
  
     单击**“确定”**完成操作。  出现“选择数据库对象”对话框。  从此对话框中选择使用者将使用的表、视图或过程。  
  
     **提供程序**  
     选择适当的提供程序来管理数据源的连接。  主要由正在连接的数据库类型决定的提供程序类型。  单击 `Next` 按钮或单击**“连接”**选项卡。  
  
     **Connection**  
     选项卡的内容取决于您选定的提供程序。  虽然有很多类型的提供程序，但本节只介绍两个最常见提供程序之间的联系：SQL 和 ODBC 数据。  其他为此处所述的字段相类似的变体。  
  
     SQL 数据。  
  
    1.  **选择或输入服务器名称：** 单击下拉菜单，将显示所有在网络中注册的数据服务器，选择其中的一个。  
  
    2.  **输入信息登录服务器：** 输入用户名和密码登录数据服务器。  
  
    3.  **选择服务器上的数据库：**单击下拉菜单，将显示所有在数据服务器上注册的数据库，选择其中的一个。  
  
         \- 或 \-  
  
         **将数据库文件附加为数据库名称：**指定要用作数据库的文件；输入显式路径名。  
  
        > [!NOTE]
        >  “数据链接属性”对话框的“允许保存密码”功能存在安全问题。  “输入登录服务器所需的信息”中包含两个单选按钮：  
  
         **使用 Windows NT 集成安全性**  
  
         **使用指定的用户名称和密码**  
  
         如果选择“使用特定的用户名和密码”，则可以选择保存密码（使用“允许保存密码”复选框）；但是此选项不安全。  建议您选择**“使用 Windows NT 集成安全性”**；此选项因为加密了密码而很安全。  
  
         可能存在您想要选择“允许保存密码”的情形。例如，如果您释放有私有数据库解决方案的库，不应直接访问数据库而是应该改用一个中间层应用程序来验证用户（无论通过您选择何种身份验证方案），然后限制对用户可用的数据的排序。  
  
         ODBC 数据。  
  
         1.   **指定的数据源：** 您可以使用数据源名称或连接字符串。  
  
         **使用数据源名称：**此下拉列表显示您计算机中注册的数据源。  可以通过使用 [ODBC Data Source Administrator](!Alink("dasdkODBCDataSourceAdmin")).\-或\-**使用连接字符串：** 输入已获取的连接字符串，或单击**Build**按钮；出现 **选择数据源** 对话框设置时间之前的数据源。  选择文件或计算机数据源，然后单击**“确定”**。  
  
        > [!NOTE]
        >  可通过在服务器资源管理器中查看现有连接的属性获取连接字符串，也可通过在服务器资源管理器中双击**“添加连接”**创建连接。  
  
         2.  **输入信息登录服务器：** 输入用户名和密码登录数据服务器。  
  
         3.  输入要使用的初始目录。  
  
         4.  单击“测试连接”；如果测试成功，则单击**“确定”**。  如果不是，请检查您的登录信息，尝试连接另一个数据库，或尝试连接另一个数据服务器。  
  
     **高级**  
     “网络”设置： 指定 [Impersonation level](!Alink("_com_Impersonation_Levels")) （模拟客户端时服务器允许使用的模拟级别； 直接对应于 RPC 模拟级别）和“保护”级别（客户端和服务器之间发送的数据的保护级别； 直接对应于 RPC 保护级别\)。  
  
     **其他：** 在**连接超时**中，指定超时发生前允许的空闲时间的秒数。  在**访问权限**中，指定对数据连接的访问权限。  
  
     有关高级初始化属性的更多信息，请参考随每个特定 OLE DB 提供程序一起提供的文档。  
  
     **全部**  
     此选项卡显示已指定数据源和连接的初始化属性的摘要。  可编辑这些值。  
  
     单击**“确定”**完成操作。  出现“选择数据库对象”对话框。  从此对话框中选择使用者将使用的表、视图或过程。  
  
 `Class`  
 选定数据源后，根据选定的表或存储过程在此框中填充默认类名（请参见下面的“选择数据源”）。  可以编辑类名。  
  
 **.h 文件**  
 选定数据源后，根据选定的表或存储过程在此框中填充默认头类名（请参见下面的“选择数据源”）。  可编辑头文件的名称或选择现有的头文件。  
  
 **特性化**  
 此选项指定向导是使用特性还是模板声明来创建使用者类。  若选择此选项，向导将使用特性而不是模板声明（这是默认选项）。  当撤消选择此选项时，向导使用模板声明而不是特性。  
  
-   如果为使用方**“类型”**选择“表”，向导将使用 `db_source` 和 **db\_table** 特性来创建表和表访问器类声明，并使用 **db\_column** 来创建列映射，例如：  
  
    ```  
    // Inject table class and table accessor class declarations  
    [  
        db_source("<initialization_string>"),  
        db_table("dbo.Orders")  
    ]  
    ...  
    // Column map  
        [ db_column(1, status=m_dwOrderIDStatus,         length=m_dwOrderIDLength) ] LONG m_OrderID;  
        [ db_column(2, status=m_dwCustomerIDStatus,         length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];  
        ...  
    ```  
  
     而不是使用 `CTable` 模板类来声明表和表访问器类，并使用 BEGIN\_COLUMN\_MAP 和 END\_COLUMN\_MAP 宏来创建列映射，例如：  
  
    ```  
    // Table accessor class  
    class COrdersAccessor;  
    // Table class  
    class COrders : public CTable<CAccessor<COrdersAccessor> >;  
    ...  
    // Column map  
    BEGIN_COLUMN_MAP(COrderDetailsAccessor)  
        COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID,         m_dwOrderIDLength, m_dwOrderIDStatus)  
        COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID,         m_dwCustomerIDLength, m_dwCustomerIDStatus)  
        ...  
    END_COLUMN_MAP()  
    ```  
  
-   如果为使用方**“类型”**选择“命令”，向导将使用 `db_source` 和 **db\_command** 特性，并使用 **db\_column** 来创建列映射，例如：  
  
    ```  
    [  
        db_source("<initialization_string>"),  
        db_command("SQL_command")  
    ]  
    ...  
    // Column map using db_column is the same as for consumer type of 'table'  
    ```  
  
     而不是在命令类的 .h 文件中使用命令和命令访问器类声明，例如：  
  
    ```  
    Command accessor class:  
    class CListOrdersAccessor;  
    Command class:  
    class CListOrders : public CCommand<CAccessor<CListOrdersAccessor> >;  
    ...  
    // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as  
    // for consumer type of 'table'  
    ```  
  
 有关更多信息，请参见[Basic Mechanics of Attributes](../../windows/basic-mechanics-of-attributes.md)。  
  
 **Type**  
 选择这些单选按钮之一，指定使用者类是从 `CTable` 还是从 `CCommand`（默认值）派生。  
  
 **表**  
 如果要使用 `CTable` 或 **db\_table** 创建表和表访问器类声明，则选择此选项。  
  
 **Command**  
 如果要使用 `CCommand` 或 **db\_command** 创建命令和命令访问器类声明，则选择此选项。  这是默认选择。  
  
 **支持**  
 选择复选框可以指定使用者中支持的更新类型（默认为“无”）。  下列每个选项都在属性集映射中设置 [DBPROP\_IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715892.aspx) 和适当的 [DBPROP\_UPDATABILITY](https://msdn.microsoft.com/en-us/library/ms722676.aspx) 项。  
  
 **更改**  
 指定使用者支持更新行集合中的原始数据。  
  
 **Insert**  
 指定使用者支持在行集合中插入行。  
  
 **Delete**  
 指定使用者支持从行集合中删除行。  
  
## 请参阅  
 [ATL OLE DB Consumer](../../atl/reference/adding-an-atl-ole-db-consumer.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [连接字符串和数据链接 \(OLE DB\)](https://msdn.microsoft.com/en-us/library/ms718376.aspx)