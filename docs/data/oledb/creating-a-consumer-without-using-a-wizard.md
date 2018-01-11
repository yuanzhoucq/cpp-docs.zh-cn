---
title: "不使用向导创建使用者 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b31f1ad51d9015c491439650060ab3cefaf3270b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>不使用向导创建使用者
下面的示例假定 OLE DB 使用者支持添加到现有的 ATL 项目。 如果你想要将 OLE DB 使用者支持添加到 MFC 应用程序，应运行 MFC 应用程序向导，也不能创建所有支持必要时，将调用执行应用程序所需的 MFC 例程。  
  
 若要添加 OLE DB 使用者支持而不使用 ATL OLE DB 使用者向导：  
  
-   在 Stdafx.h 文件中，追加以下`#include`语句：  
  
    ```  
    #include <atlbase.h>  
    #include <atldbcli.h>  
    #include <atldbsch.h> // if you are using schema templates  
    ```  
  
 以编程方式，使用者通常会执行以下操作序列：  
  
-   创建一个将列绑定到本地变量的用户记录类。 在此示例中，`CMyTableNameAccessor`是用户记录类 (请参阅[用户记录](../../data/oledb/user-records.md))。 此类包含的列映射和参数映射。 声明中指定列映射; 中的每个字段的用户记录类的数据成员对于每个这些数据成员，还声明状态数据成员和长度数据成员。 有关详细信息，请参阅[向导生成的访问器中的字段状态数据成员](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)。  
  
    > [!NOTE]
    >  如果您编写自己的使用者，则数据变量必须早的状态和长度的变量。  
  
-   实例化的数据源和会话。 决定哪种类型的访问器和行集使用，然后实例化行集使用[CCommand](../../data/oledb/ccommand-class.md)或[CTable](../../data/oledb/ctable-class.md):  
  
    ```  
    CDataSource ds;  
    CSession ss;  
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor> >  
    ```  
  
-   调用**CoInitialize**以初始化 com。 这通常称为主要代码中。 例如:  
  
    ```  
    HRESULT hr = CoInitialize(NULL);  
    ```  
  
-   调用[cdatasource:: Open](../../data/oledb/cdatasource-open.md)或其变体之一。  
  
-   打开与数据源的连接、 打开会话，并打开和初始化行集 （和如果某个命令，也执行它）：  
  
    ```  
    hr = ds.Open();  
    hr = ss.Open(ds);  
    hr = rs.Open();            // (Open also executes the command)  
    ```  
  
-   使用的 （可选） 设置行集属性`CDBPropSet::AddProperty`并将它们传递作为参数传递给`rs.Open`。 有关如何完成此操作的示例，请参阅中的 GetRowsetProperties[使用者向导生成方法](../../data/oledb/consumer-wizard-generated-methods.md)。  
  
-   你现在可以使用行集检索/处理的数据。  
  
-   完成你的应用程序后，关闭连接、 会话和行集：  
  
    ```  
    rs.Close();  
    ss.Close();  
    ds.Close();  
    ```  
  
     如果你使用的是命令，你可能想要调用`ReleaseCommand`后**关闭**。 中的代码示例[ccommand:: Close](../../data/oledb/ccommand-close.md)演示如何调用**关闭**和`ReleaseCommand`。  
  
-   调用**CoUnInitialize**取消初始化 com。 这通常称为主要代码中。  
  
    ```  
    CoUninitialize();  
    ```  
  
## <a name="see-also"></a>请参阅  
 [创建 OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer.md)