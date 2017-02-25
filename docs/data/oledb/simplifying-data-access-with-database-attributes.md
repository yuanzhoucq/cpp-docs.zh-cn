---
title: "使用数据库特性简化数据访问 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-attr.db_param"
  - "vc-attr.db_column"
  - "vc-attr.db_accessor"
  - "vc-attr.db_command"
  - "vc-attr.db_table"
  - "vc-attr.db_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "特性 [C++], 数据访问"
  - "特性 [C++], 数据库"
  - "特性 [C++], OLE DB 使用者"
  - "数据 [C++], 简化访问"
  - "数据访问 [C++], 数据库特性"
  - "数据库特性 [C++]"
  - "数据库 [C++], 特性"
  - "OLE DB 使用者 [C++], 数据库特性"
ms.assetid: 560d2456-e307-4cb7-ba7b-4d0ed674697f
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用数据库特性简化数据访问
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题说明如何使用数据库特性简化数据库操作。  
  
 访问数据库中信息的基本方法是针对数据库中的特定表创建命令（或表）类和用户记录类。  数据库特性简化了先前必须进行的一些模板声明。  
  
 为说明数据库特性的用法，下面各节介绍两个等效的表和用户记录类声明：第一个使用特性，第二个则使用 OLE DB 模板。  这类声明代码通常放置在头文件中，以表或命令对象命名，例如 Authors.h。  
  
 通过比较这两个文件，便可以看出使用特性是多么简单。  两者的差异包括：  
  
-   如果使用特性，则只需声明一个类：`CAuthors`，而使用模板则必须声明两个类：`CAuthorsNoAttrAccessor` 和 `CAuthorsNoAttr`。  
  
-   特性化版本中的 `db_source` 调用等效于模板声明中的 `OpenDataSource()` 调用。  
  
-   特性化版本中的 **db\_table** 调用等效于以下模板声明：  
  
    ```  
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor> >  
    ```  
  
-   特性化版本中的 **db\_column** 调用等效于模板声明中的列映射（请参见 `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`）。  
  
 特性将为您插入用户记录类声明。  此用户记录类等效于模板声明中的 `CAuthorsNoAttrAccessor`。  如果表类为 `CAuthors`，则插入的用户记录类命名为 `CAuthorsAccessor`，并且只能在插入的代码中查看其声明。  有关更多信息，请参见[用户记录](../../data/oledb/user-records.md)中的“特性插入的用户记录类”。  
  
 注意，在特性化代码和模板化代码中，都必须使用 `CDBPropSet::AddProperty` 设置行集合属性。  
  
 有关本主题中所讨论特性的信息，请参见 [OLE DB 使用者特性](../../windows/ole-db-consumer-attributes.md)。  
  
## 使用特性进行表和访问器声明  
 以下代码在表类上调用 `db_source` 和 **db\_table**。  `db_source` 指定要使用的数据源和连接。  **db\_table** 插入适当的模板代码以声明表类。  **db\_column** 指定列映射并插入访问器声明。  可以使用支持 ATL 的任何项目中的 OLE DB 使用者特性。  
  
 以下是使用特性进行的表和访问器声明：  
  
```  
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
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
   [ db_column(1, status=m_dwAuIDStatus, length=m_dwAuIDLength) ] LONG m_AuID;  
   [ db_column(2, status=m_dwAuthorStatus, length=m_dwAuthorLength) ] TCHAR m_Author[51];  
   [ db_column(3, status=m_dwYearBornStatus, length=m_dwYearBornLength) ] SHORT m_YearBorn;  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
   }  
};  
```  
  
## 使用模板的表和访问器声明  
 以下是使用模板的表和访问器声明。  
  
```  
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
class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor> >  
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
  
## 请参阅  
 [OLE DB Consumer Attributes](../../windows/ole-db-consumer-attributes.md)   
 [Attributes Walkthroughs](http://msdn.microsoft.com/zh-cn/73df1d5d-261a-4521-98fb-06dcbf5ec0d0)