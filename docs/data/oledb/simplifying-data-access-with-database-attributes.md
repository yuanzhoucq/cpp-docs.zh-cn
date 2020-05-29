---
title: 使用数据库特性简化数据访问
ms.date: 10/19/2018
helpviewer_keywords:
- attributes [C++], database
- attributes [C++], data access
- databases [C++], attributes
- data [C++], simplifying access
- data access [C++], database attributes
- database attributes [C++]
- OLE DB consumers [C++], database attributes
- attributes [C++], OLE DB consumer
ms.assetid: 560d2456-e307-4cb7-ba7b-4d0ed674697f
ms.openlocfilehash: d22f8a25bc7bb58f72346a15edb51f062c44e1b4
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2020
ms.locfileid: "79546175"
---
# <a name="simplifying-data-access-with-database-attributes"></a>使用数据库特性简化数据访问

本主题演示如何使用数据库属性简化数据库操作。

从数据库访问信息的基本方法是为数据库中的特定表创建命令（或表）类和用户记录类。 数据库属性简化了之前必须执行的一些模板声明。

为了演示数据库属性的使用，以下各节显示了两个等效的表和用户记录类声明：第一个使用特性，第二个使用 OLE DB 模板。 此类声明代码通常放置在一个名为的表或命令对象（例如，作者 .h）中。

通过比较这两个文件，可以看出使用特性的方法要简单得多。 不同之处在于：

- 使用特性，你只需声明一个类： `CAuthors`，使用模板时，必须声明两个： `CAuthorsNoAttrAccessor` 和 `CAuthorsNoAttr`。

- 特性化版本中的 `db_source` 调用等效于模板声明中的 `OpenDataSource()` 调用。

- 特性化版本中的 `db_table` 调用等效于以下模板声明：

    ```cpp
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>
    ```

- 特性化版本中的 `db_column` 调用等效于模板声明中的列映射（参见 `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`）。

属性为您注入用户记录类声明。 用户记录类等于模板声明中的 `CAuthorsNoAttrAccessor`。 如果表类是 `CAuthors`的，则插入的用户记录类的名称为 `CAuthorsAccessor`，并且只能在注入的代码中查看其声明。 有关详细信息，请参阅[用户记录](../../data/oledb/user-records.md)中的 "属性插入的用户记录类"。

在特性化和模板化的代码中，必须使用 `CDBPropSet::AddProperty`设置行集属性。

有关本主题中讨论的属性的信息，请参阅[OLE DB 使用者属性](../../windows/ole-db-consumer-attributes.md)。

> [!NOTE]
> 下面的 `include` 语句需要编译下面的示例：

> ```cpp
> #include <atlbase.h>
> #include <atlplus.h>
> #include <atldbcli.h>
> ```

## <a name="table-and-accessor-declaration-using-attributes"></a>使用特性的表和访问器声明

下面的代码对 table 类调用 `db_source` 和 `db_table`。 `db_source` 指定要使用的数据源和连接。 `db_table` 插入适当的模板代码以声明表类。 `db_column` 指定列映射并注入访问器声明。 可以在任何支持 ATL 的项目中使用 OLE DB 使用者属性。

下面是使用属性的表和访问器声明：

```cpp
//////////////////////////////////////////////////////////////////////
// Table and accessor declaration using attributes
// authors.h
//////////////////////////////////////////////////////////////////////

// Table class declaration
// (Note that you must provide your own connection string for db_source.)
[
   db_source(L"your connection string"),
   db_table("Authors")
]
class CAuthors
{
public:
   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;
   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;
   [db_column("1", status = "m_dwAuIDStatus", length = "m_dwAuIDLength")] LONG m_AuID;
   [db_column("2", status = "m_dwAuthorStatus", length = "m_dwAuthorLength")] TCHAR m_Author[51];
   [db_column("3", status = "m_dwYearBornStatus", length = "m_dwYearBornLength")] SHORT m_YearBorn;
   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);
   }
};
```

## <a name="table-and-accessor-declaration-using-templates"></a>使用模板的表和访问器声明

下面是使用模板的表和访问器声明。

```cpp
//////////////////////////////////////////////////////////////////////
// Table and user record class declaration using templates
// authors.h
//////////////////////////////////////////////////////////////////////

// User record class declaration
class CAuthorsNoAttrAccessor
{
public:
   DWORD m_dwAuIDStatus;
   DWORD m_dwAuthorStatus;
   DWORD m_dwYearBornStatus;
   DWORD m_dwAuIDLength;
   DWORD m_dwAuthorLength;
   DWORD m_dwYearBornLength;
   LONG m_AuID;
   TCHAR m_Author[51];
   SHORT m_YearBorn;
   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);
   }
   HRESULT OpenDataSource()
   {
      CDataSource _db;

HRESULT hr;
      hr = _db.OpenFromInitializationString(L"your connection string");
      if (FAILED(hr))
      {
#ifdef _DEBUG
         AtlTraceErrorRecords(hr);
#endif
         return hr;
      }
      return m_session.Open(_db);
   }
   void CloseDataSource()
   {
      m_session.Close();
   }
   operator const CSession&()
   {
      return m_session;
   }
   CSession m_session;
   BEGIN_COLUMN_MAP(CAuthorsNoAttrAccessor)
      COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, m_dwAuIDLength, m_dwAuIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, m_dwAuthorLength, m_dwAuthorStatus)
      COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, m_dwYearBornLength, m_dwYearBornStatus)
   END_COLUMN_MAP()
};
class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>
{
public:
   HRESULT OpenAll()
   {
HRESULT hr;
      hr = OpenDataSource();
      if (FAILED(hr))
         return hr;
      __if_exists(GetRowsetProperties)
      {
         CDBPropSet propset(DBPROPSET_ROWSET);
         __if_exists(HasBookmark)
         {
            propset.AddProperty(DBPROP_IRowsetLocate, true);
         }
         GetRowsetProperties(&propset);
         return OpenRowset(&propset);
      }
      __if_not_exists(GetRowsetProperties)
      {
         __if_exists(HasBookmark)
         {
            CDBPropSet propset(DBPROPSET_ROWSET);
            propset.AddProperty(DBPROP_IRowsetLocate, true);
            return OpenRowset(&propset);
         }
      }
      return OpenRowset();
   }
   HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)
   {
HRESULT hr = Open(m_session, "Authors", pPropSet);
#ifdef _DEBUG
      if(FAILED(hr))
         AtlTraceErrorRecords(hr);
#endif
      return hr;
   }
   void CloseAll()
   {
      Close();
      CloseDataSource();
   }
};
```

## <a name="see-also"></a>另请参阅

[OLE DB 使用者特性](../../windows/ole-db-consumer-attributes.md)
