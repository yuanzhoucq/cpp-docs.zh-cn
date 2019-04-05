---
title: 不使用向导创建使用者
ms.date: 10/12/2018
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
ms.openlocfilehash: 029fe6866df81d366cc3bc15096f638791faa413
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030415"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>不使用向导创建使用者

下面的示例假定您要将 OLE DB 使用者支持添加到现有的 ATL 项目。 如果你想要将 OLE DB 使用者支持添加到 MFC 应用程序，则应运行**MFC 应用程序向导**，这将创建所有支持必要然后调用执行应用程序所需的 MFC 例程。

若要添加的 OLE DB 使用者支持而无需使用**ATL OLE DB 使用者向导**:

- 在 pch.h 文件中，追加以下`#include`语句：

    ```cpp
    #include <atlbase.h>
    #include <atldbcli.h>
    #include <atldbsch.h> // if you are using schema templates
    ```

以编程方式，使用者通常执行以下一系列操作：

1. 创建将列绑定到本地变量的用户记录类。 在此示例中，`CMyTableNameAccessor`是用户记录类 (请参阅[用户记录](../../data/oledb/user-records.md))。 此类包含的列映射和参数映射。 声明中指定列映射; 中的每个字段的用户记录类的数据成员对于每个这些成员，还声明状态数据成员和长度数据成员。 有关详细信息，请参阅[向导生成的取值函数中的字段状态数据成员](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)。

    > [!NOTE]
    > 如果您编写自己的使用者，则数据变量必须在状态和长度变量之前。

- 实例化的数据源和会话。 决定哪种类型的访问器和行集使用，然后实例化行集使用[CCommand](../../data/oledb/ccommand-class.md)或[CTable](../../data/oledb/ctable-class.md):

    ```cpp
    CDataSource ds;
    CSession ss;
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>
    ```

- 调用`CoInitialize`初始化 com。 这称为主代码中。 例如：

    ```cpp
    HRESULT hr = CoInitialize(NULL);
    ```

- 调用[cdatasource:: Open](../../data/oledb/cdatasource-open.md)或其中一个及其变体。

- 打开与数据源的连接、 打开会话，并打开和初始化行集 （和如果一个命令，还执行它）：

    ```cpp
    hr = ds.Open();
    hr = ss.Open(ds);
    hr = rs.Open();            // (Open also executes the command)
    ```

- 使用的 （可选） 设置行集属性`CDBPropSet::AddProperty`并将它们作为参数传递`rs.Open`。 有关如何完成此操作的示例，请参阅`GetRowsetProperties`中[使用者向导生成方法](../../data/oledb/consumer-wizard-generated-methods.md)。

- 现在可以使用行集来检索/操作数据。

- 完成你的应用程序后，关闭连接、 会话和行集：

    ```cpp
    rs.Close();
    ss.Close();
    ds.Close();
    ```

   如果使用的命令，你可能想要调用`ReleaseCommand`后`Close`。 中的代码示例[ccommand:: Close](../../data/oledb/ccommand-close.md)演示了如何调用`Close`和`ReleaseCommand`。

- 调用`CoUnInitialize`取消初始化 com。 这称为主代码中。

    ```cpp
    CoUninitialize();
    ```

## <a name="see-also"></a>请参阅

[创建 OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer.md)