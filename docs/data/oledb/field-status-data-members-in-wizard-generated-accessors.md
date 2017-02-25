---
title: "向导生成的访问器中的字段状态数据成员 | Microsoft Docs"
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
  - "OLE DB 模板中的字段状态"
  - "OLE DB 使用者模板, 字段状态"
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 向导生成的访问器中的字段状态数据成员
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用“ATL OLE DB 使用者向导”创建使用者时，该向导在用户记录类中为您在列映射中指定的每个字段生成一个数据成员。  每个数据成员的类型均为 `DWORD`，并且包含一个与其各自的字段相对应的状态值。  
  
 例如，对于数据成员 *m\_OwnerID*，向导为字段状态 \(*dwOwnerIDStatus*\) 生成一个附加数据成员，并为字段长度生成另一个数据成员 \(*dwOwnerIDLength*\)。  它还生成具有 `COLUMN_ENTRY_LENGTH_STATUS` 项的列映射。  
  
 这显示在以下代码中：  
  
```  
[db_source("insert connection string")]  
[db_command(" \  
   SELECT \  
      Au_ID, \  
      Author, \  
      `Year Born`, \  
      FROM Authors")]  
  
class CAuthors  
{  
public:  
  
   // The following wizard-generated data members contain status   
   // values for the corresponding fields in the column map. You   
   // can use these values to hold NULL values that the database   
   // returns or to hold error information when the compiler returns   
   // errors. See "Field Status Data Members in Wizard-Generated   
   // Accessors" in the Visual C++ documentation for more information   
   // on using these fields.  
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
  
   // The following wizard-generated data members contain length  
   // values for the corresponding fields in the column map.  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
  
BEGIN_COLUMN_MAP(CAuthorsAccessor)  
   COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, dwAuIDLength, dwAuIDStatus)  
   COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, dwAuthorLength, dwAuthorStatus)  
   COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, dwYearBornLength, dwYearBornStatus)  
END_COLUMN_MAP()  
  
   [ db_column(1, status=m_dwAuIDStatus, length=m_dwAuIDLength) ] LONG m_AuID;  
   [ db_column(2, status=m_dwAuthorStatus, length=m_dwAuthorLength) ] TCHAR m_Author[51];  
   [ db_column(3, status=m_dwYearBornStatus, length=m_dwYearBornLength) ] SHORT m_YearBorn;  
  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
      pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
   }  
};  
```  
  
> [!NOTE]
>  如果您修改用户记录类或编写自己的使用者，则数据变量必须出现在状态变量和长度变量的前面。  
  
 可以将这些状态值用于调试目的。  如果由“ATL OLE DB 使用者向导”生成的代码生成编译错误，如 **DB\_S\_ERRORSOCCURRED** 或 **DB\_E\_ERRORSOCCURRED**，则应首先查看字段状态数据成员的当前值。  那些具有非零值的数据成员对应于有问题的列。  
  
 还可以使用状态值为特定字段设置 NULL 值。  如果想用 NULL 而不是用零来鉴别某一字段值，则这样做将会对您有所帮助。  NULL 是有效值还是特殊值以及应用程序应如何处理该值都由您决定。  OLE DB 将 **DBSTATUS\_S\_ISNULL** 定义为指定一般 NULL 值的正确方法。  如果使用者读取数据，但其值为空，则状态字段设置为 **DBSTATUS\_S\_ISNULL**。  如果使用者想设置 NULL 值，则该使用者将在调用提供程序之前将状态值设置为 **DBSTATUS\_S\_ISNULL**。  
  
 接下来，打开 Oledb.h 并搜索 **DBSTATUSENUM**。  然后，即可将非零状态的数值与 **DBSTATUSENUM** 枚举值进行匹配。  如果枚举名称不能够充分说明哪里出现了错误，那么，请参见 [OLE DB 程序员指南](http://go.microsoft.com/fwlink/?LinkId=121548)中的“绑定数据值"一节中的“状态”主题。  本主题包含获取或设置数据时所用的状态值表。  有关长度值的信息，请参见同一节中的“长度”主题。  
  
## 检索列的长度或状态  
 可以检索变长列的长度或某列的状态（例如，检查 **DBSTATUS\_S\_ISNULL**）：  
  
-   若要获取长度，请使用 `COLUMN_ENTRY_LENGTH` 宏。  
  
-   若要获取状态，请使用 `COLUMN_ENTRY_STATUS` 宏。  
  
-   若要同时获取两者，请使用 `COLUMN_ENTRY_LENGTH_STATUS`，如下所示。  
  
```  
class CProducts  
{  
public:  
   char      szName[40];  
   long      nNameLength;  
   DBSTATUS   nNameStatus;  
  
BEGIN_COLUMN_MAP(CProducts)  
// Bind the column to CProducts.m_ProductName.  
// nOrdinal is zero-based, so the column number of m_ProductName is 1.  
   COLUMN_ENTRY_LENGTH_STATUS(1, szName, nNameLength, nNameStatus)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CProducts > > product;  
  
product.Open(session, "Product");  
while (product.MoveNext() == S_OK)  
{  
   // Check the product name isn't NULL before tracing it  
   if (product.nNameStatus == DBSTATUS_S_OK)  
      ATLTRACE("%s is %d characters\n", szName, nNameLength);  
}  
```  
  
 使用 `CDynamicAccessor` 时，自动绑定长度和状态。  若要检索长度和状态值，请使用 `GetLength` 和 **GetStatus** 成员函数。  
  
## 请参阅  
 [使用 OLE DB 使用者模板](../../data/oledb/working-with-ole-db-consumer-templates.md)