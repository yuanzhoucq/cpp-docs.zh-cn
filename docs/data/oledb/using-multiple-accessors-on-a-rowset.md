---
title: 在行集上使用多个访问器 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a30108ec344091631094cd55f6a3bd3f0f4a4a54
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="using-multiple-accessors-on-a-rowset"></a>在一个行集合上使用多个访问器
有三种基本方案，你需要使用多个访问器：  
  
-   **多个读/写行集。** 在此方案中，必须具有主键的表。 你想要能够读取的行，包括主键中的所有列。 你还想要能够将数据写入到除主键外的所有列，（因为无法写入的主键列）。 在这种情况下，你设置两个访问器：  
  
    -   访问器 0 包含的所有列。  
  
    -   访问器 1 包含除主键外的所有列。  
  
-   **性能。** 在此方案中，一个或多个列包含大量的数据，例如，图形、 声音，或视频文件。 每次移动到某一行时，您可能不想要检索具有大型数据文件中，列因为这样做会降低应用程序的性能。  
  
     你可以设置单独的访问器在其第一个访问器包含除对大型数据的所有列，它从这些列中自动; 检索数据这是自动访问器。 第二个访问器检索仅包含大型数据的列，但它不会检索数据来自此列自动。 你可以更新或按需获取大数据的其他方法。  
  
    -   访问器 0 是一个自动访问器;它将检索除对大型数据的所有列。  
  
    -   访问器 1 不是一个自动的访问器;它将检索大型数据的列。  
  
     使用自动参数指定访问器是否为自动访问器。  
  
-   **多个 ISequentialStream 列。** 在此方案中，你有多个列包含`ISequentialStream`数据。 但是，每个访问器将限定为一个`ISequentialStream`数据流。 若要解决此问题，设置多个访问器中，各包含一个`ISequentialStream`指针。  
  
 通常情况下创建访问器使用[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。 你还可以使用[db_accessor](../../windows/db-accessor.md)属性。 (访问器中进行了描述进一步[用户记录](../../data/oledb/user-records.md)。)宏或属性指定访问器是自动还是非自动访问器：  
  
-   在自动访问器中，移动方法如**MoveFirst**， `MoveLast`， `MoveNext`，和`MovePrev`所有自动指定列中检索数据。 访问器 0 应自动访问器。  
  
-   在非自动访问器中中, 检索不会发生之前显式如调用的方法**更新**，**插入**，**提取**，或**删除**. 在上面所述的方案，你可能不想要检索每次移动的所有列。 可以将一个或多个列放在单独的访问器，并使其成为非自动访问器中，如下所示。  
  
 下面的示例使用多个访问器读取和写入到使用多个访问器的 SQL Server pubs 数据库的作业表。 这是多个访问器; 的最常见用途请参阅上述"多个读/写行集"方案。  
  
 用户记录类是，如下所示。 设置两个访问器： 访问器 0 包含仅的主键列 (ID) 和访问器 1 包含其他列。  
  
```  
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
  
 主要的代码如下所示。 调用`MoveNext`自动从使用访问器 0 的主键列 ID 检索数据。 请注意如何**插入**附近使用访问器 1 以避免写入主键列的方法。  
  
```  
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
 [使用访问器](../../data/oledb/using-accessors.md)   
 [用户记录](../../data/oledb/user-records.md)