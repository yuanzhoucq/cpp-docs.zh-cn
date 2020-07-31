---
title: 提取数据
ms.date: 10/19/2018
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
ms.openlocfilehash: 919eb059f5d3f29d491bf7a6598b0c77163bd783
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184639"
---
# <a name="fetching-data"></a>提取数据

打开数据源、会话和行集对象之后，就可以提取数据了。 可能需要绑定列，具体取决于所使用的访问器类型。

## <a name="to-fetch-data"></a>提取数据

1. 使用适当的 "**打开**" 命令打开行集。

1. 如果你使用 `CManualAccessor` 的是，请绑定输出列（如果尚未这样做）。 下面的示例摘自[DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)示例。 若要绑定列，请调用 `GetColumnInfo` ，然后使用绑定创建访问器，如以下示例中所示：

    ```cpp
    // From the DBViewer Sample CDBTreeView::OnQueryEdit
    // Get the column information
    ULONG ulColumns       = 0;
    DBCOLUMNINFO* pColumnInfo  = NULL;
    LPOLESTR pStrings      = NULL;
    if (rs.GetColumnInfo(&ulColumns, &pColumnInfo, &pStrings) != S_OK)
        ThrowMyOLEDBException(rs.m_pRowset, IID_IColumnsInfo);
    struct MYBIND* pBind = new MYBIND[ulColumns];
    rs.CreateAccessor(ulColumns, &pBind[0], sizeof(MYBIND)*ulColumns);
    for (ULONG l=0; l<ulColumns; l++)
    rs.AddBindEntry(l+1, DBTYPE_STR, sizeof(TCHAR)*40, &pBind[l].szValue, NULL, &pBind[l].dwStatus);
    rs.Bind();
    ```

1. 编写 **`while`** 循环以检索数据。 在循环中，调用 `MoveNext` 以使游标前进并针对 S_OK 测试返回值，如下面的示例中所示：

    ```cpp
    while (rs.MoveNext() == S_OK)
    {
        // Add code to fetch data here
        // If you are not using an auto accessor, call rs.GetData()
    }
    ```

1. 在 **`while`** 循环中，可以根据访问器类型提取数据。

   - 如果使用[CAccessor](../../data/oledb/caccessor-class.md)类，则应具有包含数据成员的用户记录。 您可以使用这些数据成员访问数据，如以下示例中所示：

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members directly. In this case, m_nFooID
            // is declared in a user record that derives from
            // CAccessor
            wsprintf_s("%d", rs.m_nFooID);
        }
        ```

   - 如果使用 `CDynamicAccessor` 或 `CDynamicParameterAccessor` 类，则可以通过使用访问函数和来提取数据 `GetValue` `GetColumn` ，如下面的示例中所示。 如果要确定所使用的数据类型，请使用 `GetType` 。

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the dynamic accessor functions to retrieve your data.

            ULONG ulColumns = rs.GetColumnCount();
            for (ULONG i=0; i<ulColumns; i++)
            {
                rs.GetValue(i);
            }
        }
        ```

   - 如果你使用 `CManualAccessor` ，则必须指定你自己的数据成员、自行绑定并直接访问这些成员，如以下示例中所示：

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members you specified in the calls to
            // AddBindEntry.

            wsprintf_s("%s", szFoo);
        }
        ```

## <a name="see-also"></a>另请参阅

[使用 OLE DB 使用者模板](../../data/oledb/working-with-ole-db-consumer-templates.md)
