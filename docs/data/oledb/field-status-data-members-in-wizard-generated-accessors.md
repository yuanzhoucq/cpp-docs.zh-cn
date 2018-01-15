---
title: "字段中向导生成的访问器的状态数据成员 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5b11350adfa70f38824744054df01d3d657e7474
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>向导生成的访问器中的字段状态数据成员
当你使用 ATL OLE DB 使用者向导创建使用者时，向导将在指定列映射中每个字段的用户记录类生成的数据成员。 每个数据成员是类型`DWORD`并包含其各自的字段相对应的状态值。  
  
 例如，对于数据成员*m_OwnerID*，该向导将生成字段状态的其他数据成员 (*dwOwnerIDStatus*) 和另一个输入字段长度 (*dwOwnerIDLength*). 它还将生成具有的列映射`COLUMN_ENTRY_LENGTH_STATUS`条目。  
  
 以下代码所示：  
  
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
>  如果修改用户记录类或编写自己的使用者，则数据变量必须在状态和长度变量之前出现。  
  
 出于调试目的，可以使用 status 值。 如果由 ATL OLE DB 使用者向导生成的代码将生成编译错误，如**DB_S_ERRORSOCCURRED**或**DB_E_ERRORSOCCURRED**，你应首先看一下字段状态的当前值数据成员。 具有非零值对应于有问题的列。  
  
 Status 值还可用于设置特定字段的 NULL 值。 这样可帮助你在想要将字段值为 NULL，而不是零区分开来的情况下。 它是您要决定 NULL 是否是有效的值或特殊值，并决定你的应用程序应如何处理它。 OLE DB 定义**是 DBSTATUS_S_ISNULL**作为的指定泛型的 NULL 值的正确方法。 如果使用者读取数据且值为 null，将状态字段设置为**是 DBSTATUS_S_ISNULL**。 如果使用者想要设置一个 NULL 值，使用者会将 status 值设置为**是 DBSTATUS_S_ISNULL**之前调用提供程序。  
  
 接下来，打开 Oledb.h 并搜索**DBSTATUSENUM**。 然后可以针对的非零状态的数字值匹配**DBSTATUSENUM**枚举值。 如果枚举名称不足以告诉你问题的原因，请参阅中的"绑定数据值"部分的"状态"主题[OLE DB 程序员指南](http://go.microsoft.com/fwlink/p/?linkid=121548)。 本主题包含的 status 值获取或设置数据时使用的表。 有关长度值的信息，请参阅同一部分中的"Length"主题。  
  
## <a name="retrieving-the-length-or-status-of-a-column"></a>检索的长度或列的状态  
 你可以检索可变长度列的长度或列的状态 (检查**是 DBSTATUS_S_ISNULL**，例如):  
  
-   若要获取长度，请使用`COLUMN_ENTRY_LENGTH`宏。  
  
-   若要获取的状态，使用`COLUMN_ENTRY_STATUS`宏。  
  
-   若要获取这两项，使用`COLUMN_ENTRY_LENGTH_STATUS`，如下所示。  
  
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
  
 当你使用`CDynamicAccessor`，长度和状态将为你自动绑定。 若要检索的长度和状态的值，使用`GetLength`和**GetStatus**成员函数。  
  
## <a name="see-also"></a>请参阅  
 [使用 OLE DB 使用者模板](../../data/oledb/working-with-ole-db-consumer-templates.md)