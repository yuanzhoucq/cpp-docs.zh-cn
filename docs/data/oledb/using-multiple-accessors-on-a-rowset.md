---
title: "在一个行集合上使用多个访问器 | Microsoft Docs"
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
  - "访问器 [C++], 行集合"
  - "BEGIN_ACCESSOR 宏"
  - "BEGIN_ACCESSOR 宏, 多个访问器"
  - "行集合 [C++], 多个访问器"
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 在一个行集合上使用多个访问器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

有三种基本方案需要使用多个访问器：  
  
-   **多个读\/写行集合。**在此方案中，有一个带主键的表。  希望能够读取行中的所有列，包括主键。  还希望能够将数据写入除主键外（因为不能向主键列写入）的所有列。  在此情况下，设置两个访问器：  
  
    -   访问器 0 包含所有列。  
  
    -   访问器 1 包含除主键外的所有列。  
  
-   **性能。**此方案中，一列或多列包含大量数据（例如，图形、声音或视频文件）。  每次移动到一行时，可能不希望检索带有大型数据文件的列，原因是这样做会降低应用程序的性能。  
  
     可以设置单独的访问器，其中第一个访问器包含除带有大数据的列以外的所有列，并且它自动从这些列中检索数据；这就是自动访问器。  第二个访问器仅检索包含大数据的列，但是它不自动从此列中检索数据。  可以用其他方法根据需要更新或获取大数据。  
  
    -   访问器 0 是自动访问器；它检索除带有大数据的列以外的所有列。  
  
    -   访问器 1 不是自动访问器；它检索带有大数据的列。  
  
     使用自动参数来指定访问器是否为自动访问器。  
  
-   **多个 ISequentialStream 列。**此方案中，有多个列包含 `ISequentialStream` 数据。  但是，每个访问器被限制到一个 `ISequentialStream` 数据流。  若要解决此问题，请设置若干访问器，每个访问器包含一个 `ISequentialStream` 指针。  
  
 通常使用 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md) 和 [END\_ACCESSOR](../../data/oledb/end-accessor.md) 宏创建访问器。  还可以使用 [db\_accessor](../../windows/db-accessor.md) 特性。（在[用户记录](../../data/oledb/user-records.md)中进一步描述了访问器。）宏或特性指定访问器是自动访问器还是非自动访问器：  
  
-   在自动访问器中，移动方法（如 **MoveFirst**、`MoveLast`、`MoveNext` 和 `MovePrev`）自动检索所有指定列的数据。  访问器 0 应为自动访问器。  
  
-   在非自动访问器中，直到显式调用方法（如 **Update**、**Insert**、**Fetch** 或 **Delete**）时才会发生检索。  在上面描述的方案中，可能不希望每次移动时都检索所有列。  可以将一列或多列放在单独的访问器中并使其成为非自动访问器，如下所示。  
  
 下面的示例通过多个访问器读写使用多个访问器的 SQL Server pubs 数据库的 jobs 表。  这是多个访问器的最常见用法；请参见上面的“多个读\/写行集合”方案。  
  
 用户记录类如下所示。  它设置两个访问器：访问器 0 仅包含主键列 ID，访问器 1 包含其他列。  
  
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
  
 主代码如下所示。  调用 `MoveNext` 会自动使用访问器 0 从主键列 ID 中检索数据。  注意邻近结尾的 **Insert** 方法是如何使用访问器 1 避免向主键列写入的。  
  
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
            CTable<CAccessor<CJobs> > jobs;  
  
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
  
## 请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)   
 [用户记录](../../data/oledb/user-records.md)