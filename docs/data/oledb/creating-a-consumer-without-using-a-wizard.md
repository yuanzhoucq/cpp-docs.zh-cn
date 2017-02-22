---
title: "不使用向导创建使用者 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 使用者, 创建"
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 不使用向导创建使用者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下面的示例假定您向现有的 ATL 项目中添加 OLE DB 使用者支持。  如果要向 MFC 应用程序中添加 OLE DB 使用者支持，应运行“MFC 应用程序向导”，该向导创建所有必要的支持并调用执行此应用程序所需的 MFC 例程。  
  
 不使用“ATL OLE DB 使用者向导”添加 OLE DB 使用者支持：  
  
-   在 Stdafx.h 文件中，追加下面的 `#include` 语句：  
  
    ```  
    #include <atlbase.h>  
    #include <atldbcli.h>  
    #include <atldbsch.h> // if you are using schema templates  
    ```  
  
 使用者通常以编程方式执行以下操作序列：  
  
-   创建将列绑定到局部变量的用户记录类。  在此示例中，`CMyTableNameAccessor` 是用户记录类（请参见[用户记录](../../data/oledb/user-records.md)）。  此类包含列映射和参数映射。  在用户记录类中，为在列映射中指定的每个字段声明数据成员；对于这些数据成员中的每一个，还声明一个状态数据成员和一个长度数据成员。  有关更多信息，请参见 [向导生成的访问器中的字段状态数据成员](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)。  
  
    > [!NOTE]
    >  如果您编写自己的使用者，则数据变量必须位于状态变量与长度变量之前。  
  
-   实例化一个数据源和一个会话。  决定要使用的访问器和行集合的类型，然后使用 [CCommand](../../data/oledb/ccommand-class.md) 或 [CTable](../../data/oledb/ctable-class.md) 实例化一个行集合：  
  
    ```  
    CDataSource ds;  
    CSession ss;  
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor> >  
    ```  
  
-   调用 **CoInitialize** 以初始化 COM。  这通常是在主代码中调用的。  例如：  
  
    ```  
    HRESULT hr = CoInitialize(NULL);  
    ```  
  
-   调用 [CDataSource::Open](../../data/oledb/cdatasource-open.md) 或它的一个变体。  
  
-   打开一个到数据源的连接，打开会话，然后打开并初始化行集合（如果是命令，还执行它）：  
  
    ```  
    hr = ds.Open();  
    hr = ss.Open(ds);  
    hr = rs.Open();            // (Open also executes the command)  
    ```  
  
-   还可以根据需要使用 `CDBPropSet::AddProperty` 设置行集合属性，并且将它们作为参数传递给 `rs.Open`。  有关如何完成此操作的示例，请参见 [使用者向导生成的方法](../../data/oledb/consumer-wizard-generated-methods.md)中的“GetRowsetProperties”。  
  
-   现在可以使用该行集合检索\/操作数据。  
  
-   当完成应用程序时，关闭连接、会话和行集合：  
  
    ```  
    rs.Close();  
    ss.Close();  
    ds.Close();  
    ```  
  
     如果使用的是命令，则可能要在 **Close** 之后调用 `ReleaseCommand`。  [CCommand::Close](../../data/oledb/ccommand-close.md) 中的代码示例说明如何调用 **Close** 和 `ReleaseCommand`。  
  
-   调用 **CoUnInitialize** 以取消初始化 COM。  这通常是在主代码中调用的。  
  
    ```  
    CoUninitialize();  
    ```  
  
## 请参阅  
 [创建 OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer.md)