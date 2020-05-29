---
title: 不使用向导创建使用者
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
ms.openlocfilehash: fff4146681e31f0f1fea9fbaa559de7c722740d2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211453"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>不使用向导创建使用者

下面的示例假定要向现有 ATL 项目添加 OLE DB 使用者支持。 若要向 MFC 应用程序添加 OLE DB 使用者支持，应运行 MFC 应用程序向导，这会创建所有必要的支持，并调用执行应用程序所需的 MFC 例程。

若要在不使用 ATL OLE DB 使用者向导的情况下添加 OLE DB 使用者支持，请执行以下操作：

- 在*pch*文件中追加以下 `#include` 语句：

    ```cpp
    #include <atlbase.h>
    #include <atldbcli.h>
    #include <atldbsch.h> // if you are using schema templates
    ```

使用者通常以编程方式执行以下一系列操作：

1. 创建将列绑定到本地变量的用户记录类。 在此示例中，`CMyTableNameAccessor` 是用户记录类（请参阅[用户记录](../../data/oledb/user-records.md)）。 此类包含列映射和参数映射。 在用户记录类中为你在列映射中指定的每个字段声明数据成员；对于每个数据成员，还声明状态数据成员和长度数据成员。 有关详细信息，请参阅[向导生成的取值函数中的字段状态数据成员](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)。

    > [!NOTE]
    > 如果你编写自己的使用者，数据变量必须位于状态变量和长度变量前面。

- 实例化数据源和会话。 确定要使用什么类型的取值函数和行集，然后使用 [CCommand](../../data/oledb/ccommand-class.md) 或 [CTable](../../data/oledb/ctable-class.md) 实例化行集：

    ```cpp
    CDataSource ds;
    CSession ss;
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>
    ```

- 调用 `CoInitialize` 来初始化 COM。 调用是在主代码中进行。 例如：

    ```cpp
    HRESULT hr = CoInitialize(NULL);
    ```

- 调用 [CDataSource::Open](../../data/oledb/cdatasource-open.md) 或其变体之一。

- 打开与数据源的连接，打开会话，然后打开并初始化行集（如果是命令的话，还要执行它）：

    ```cpp
    hr = ds.Open();
    hr = ss.Open(ds);
    hr = rs.Open();            // (Open also executes the command)
    ```

- （可选）使用 `CDBPropSet::AddProperty` 设置行集属性，并将它们作为参数传递给 `rs.Open`。 有关如何完成此操作的示例，请参阅`GetRowsetProperties`使用者向导生成的方法[中的“](../../data/oledb/consumer-wizard-generated-methods.md)”。

- 现在可以使用行集来检索/控制数据了。

- 完成应用程序后，关闭连接、会话和行集：

    ```cpp
    rs.Close();
    ss.Close();
    ds.Close();
    ```

   如果使用的是命令，建议在 `ReleaseCommand` 后面调用 `Close`。 [CCommand::Close](../../data/oledb/ccommand-close.md) 中的代码示例展示了如何调用 `Close` 和 `ReleaseCommand`。

- 调用 `CoUnInitialize` 来取消初始化 COM。 调用是在主代码中进行。

    ```cpp
    CoUninitialize();
    ```

## <a name="see-also"></a>另请参阅

[创建 OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer.md)
