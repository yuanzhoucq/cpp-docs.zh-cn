---
title: 在一个行集合上使用多个访问器
ms.date: 10/24/2018
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
ms.openlocfilehash: 3ce150375b98c697c32767001911eade53ed2f8c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522020"
---
# <a name="using-multiple-accessors-on-a-rowset"></a>在一个行集合上使用多个访问器

有三种基本方案，需要在其中使用多个访问器：

- **多个读/写行集。** 在此方案中，必须具有主键的表。 你想要读取的行，其中包括主键中的所有列。 您还希望能够将数据写入除为主键的所有列 （因为无法都写入主键列）。 在这种情况下，你设置两个访问器：

  - 访问器 0 包含的所有列。

  - 访问器 1 包含除为主键的所有列。

- **性能。** 在此方案中，一个或多个列具有大量的数据，例如，图形、 声音或视频文件。 每次移动到某一行时，可能不想要检索列与大型数据文件，因为这样做将会减慢应用程序的性能。

  你可以设置单独的访问器中的第一个访问器包含除具有大型数据的所有列，并从这些列检索数据自动保存功能。第一个访问器是自动访问器。 第二个访问器检索仅保存大型数据的列，但它不会自动从该列检索数据。 您可以更新或按需获取大型数据的其他方法。

  - 访问器 0 是一个自动访问器;它将检索除具有较大的数据的所有列。

  - 访问器 1 不是自动的访问器;它将检索大型数据的列。

  使用自动参数来指定访问器是否为自动访问器。

- **多个 ISequentialStream 列。** 在此方案中，已多个列保存`ISequentialStream`数据。 但是，每个访问器仅限于一个`ISequentialStream`数据流。 若要解决此问题，设置多个取值函数，每个都拥有一个`ISequentialStream`指针。

通常情况下创建使用访问器[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)并[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。 此外可以使用[db_accessor](../../windows/db-accessor.md)属性。 (访问器中进行了描述进一步[用户记录](../../data/oledb/user-records.md)。)宏或该属性指定访问器是自动或非自动访问器：

- 在自动访问器中，如移动方法`MoveFirst`， `MoveLast`， `MoveNext`，和`MovePrev`对所有自动指定列中检索数据。 访问器 0 应自动访问器。

- 检索显式如调用的方法会执行非自动访问器中`Update`， `Insert`， `Fetch`，或`Delete`。 在上面所述方案中，您可能不想要检索每次移动的所有列。 可以将一个或多个列放在单独的访问器，并确保一个非自动访问器中，这样做，如下所示。

以下示例使用多个访问器读取和写入到 SQL Server pubs 数据库使用多个访问器的作业表。 此示例中是最常用的多个访问器;请参阅上述"多个读/写行集"方案。

用户记录类如下所示。 设置两个访问器： 访问器 0 包含仅的主键列 (ID) 和访问器 1 包含其他列。

```cpp
class CJobs
{
public:
    enum {
        sizeOfDescription = 51
    };

    short nID;
    char szDescription[ sizeOfDescription ];
    short nMinLvl;
    short nMaxLvl;

    DWORD dwID;
    DWORD dwDescription;
    DWORD dwMinLvl;
    DWORD dwMaxLvl;

BEGIN_ACCESSOR_MAP(CJobs, 2)
    // Accessor 0 is the automatic accessor
    BEGIN_ACCESSOR(0, true)
        COLUMN_ENTRY_STATUS(1, nID, dwID)
    END_ACCESSOR()
    // Accessor 1 is the non-automatic accessor
    BEGIN_ACCESSOR(1, true)
        COLUMN_ENTRY_STATUS(2, szDescription, dwDescription)
        COLUMN_ENTRY_STATUS(3, nMinLvl, dwMinLvl)
        COLUMN_ENTRY_STATUS(4, nMaxLvl, dwMaxLvl)
    END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

主代码如下所示。 调用`MoveNext`自动从使用访问器 0 的主键列 ID 检索数据。 请注意如何`Insert`附近使用访问器 1 以避免写入主键列的方法。

```cpp
int main(int argc, char* argv[])
{
    // Initalize COM
    ::CoInitialize(NULL);

    // Create instances of the data source and session
    CDataSource source;
    CSession session;
    HRESULT hr = S_OK;

    // Set initialization properties
    CDBPropSet dbinit(DBPROPSET_DBINIT);
    dbinit.AddProperty(DBPROP_AUTH_USERID, OLESTR("my_user_id"));
    dbinit.AddProperty(DBPROP_INIT_CATALOG, OLESTR("pubs"));
    dbinit.AddProperty(DBPROP_INIT_DATASOURCE, OLESTR("(local)"));

    hr = source.Open("SQLOLEDB.1", &dbinit);
    if (hr == S_OK)
    {
        hr = session.Open(source);
        if (hr == S_OK)
        {
            // Ready to fetch/access data
            CTable<CAccessor<CJobs>> jobs;

            // Set properties for making the rowset a read/write cursor
            CDBPropSet dbRowset(DBPROPSET_ROWSET);
            dbRowset.AddProperty(DBPROP_CANFETCHBACKWARDS, true);
            dbRowset.AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
            dbRowset.AddProperty(DBPROP_IRowsetChange, true);
            dbRowset.AddProperty(DBPROP_UPDATABILITY,
                DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE |
                DBPROPVAL_UP_DELETE);

            hr = jobs.Open(session, "jobs", &dbRowset);
            if (hr == S_OK)
            {
                // Calling MoveNext automatically retrieves ID
                // (using accessor 0)
                while(jobs.MoveNext() == S_OK)
                   printf_s("Description = %s\n", jobs.szDescription);

                hr = jobs.MoveFirst();
                if (hr == S_OK)
                {
                    jobs.nID = 25;
                    strcpy_s(&jobs.szDescription[0],
                             jobs.sizeOfDescription,
                             "Developer");
                    jobs.nMinLvl = 10;
                    jobs.nMaxLvl = 20;

                    jobs.dwDescription = DBSTATUS_S_OK;
                    jobs.dwID = DBSTATUS_S_OK;
                    jobs.dwMaxLvl = DBSTATUS_S_OK;
                    jobs.dwMinLvl = DBSTATUS_S_OK;

                    // Insert method uses accessor 1
                    // (to avoid writing to the primary key column)
                    hr = jobs.Insert(1);
                }
                jobs.Close();
            }
            session.Close();
        }
        source.Close();
    }

    // Uninitialize COM
    ::CoUninitialize();
    return 0;
}
```

## <a name="see-also"></a>请参阅

[使用访问器](../../data/oledb/using-accessors.md)<br/>
[用户记录](../../data/oledb/user-records.md)
