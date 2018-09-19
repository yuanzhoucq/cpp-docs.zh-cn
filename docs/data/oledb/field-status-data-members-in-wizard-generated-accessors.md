---
title: 字段中向导生成的访问器的状态数据成员 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e289e2f40326142894894dad1bfe34c801889bb3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066851"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>向导生成的访问器中的字段状态数据成员

当使用 ATL OLE DB 使用者向导来创建使用者时，向导生成数据成员中指定列映射中每个字段的用户记录类。 每个数据成员是类型的`DWORD`和包含其各自的字段相对应的状态值。  
  
例如，对于数据成员*m_OwnerID*，该向导生成的字段状态的其他数据成员 (*dwOwnerIDStatus*)，另一个用于字段长度 (*dwOwnerIDLength*). 它还会生成具有 COLUMN_ENTRY_LENGTH_STATUS 条目的列映射。  
  
以下代码所示：  
  
```cpp  
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
  
出于调试目的，可以使用的状态值。 如果在 ATL OLE DB 使用者向导生成的代码生成编译错误，例如 DB_S_ERRORSOCCURRED 或 DB_E_ERRORSOCCURRED，则应首先查看字段状态数据成员的当前值。 具有非零值对应于有问题的列。  
  
Status 值还可用于设置特定字段的 NULL 值。 这样做可帮助您在想要将字段值为 NULL，而不是零区分开来的情况下。 它是由您来决定 NULL 是否是有效的值或特殊值，并决定你的应用程序应如何处理它。 OLE DB 定义为指定的泛型的 NULL 值的正确方式 DBSTATUS_S_ISNULL。 如果使用者读取数据的值为 null，则将状态字段设置为 DBSTATUS_S_ISNULL。 如果使用者想要设置为 NULL 值，使用者将状态值设置为 DBSTATUS_S_ISNULL 之前调用提供程序。  
  
接下来，打开 Oledb.h 并搜索`DBSTATUSENUM`。 然后可以匹配的非零状态对数值`DBSTATUSENUM`枚举值。 如果枚举名称不足以告诉您怎么了，请参阅"状态"主题中的"绑定数据值"一节[OLE DB 程序员指南](/previous-versions/windows/desktop/ms713643\(v=vs.85\))。 本主题包含的状态时使用的值获取或设置数据的表。 有关长度值的信息，请参阅中的同一部分的"长度"主题。  
  
## <a name="retrieving-the-length-or-status-of-a-column"></a>检索的长度或列的状态  

您可以检索可变长度列的长度或列 （若要检查为 DBSTATUS_S_ISNULL，例如） 的状态：  
  
- 若要获取长度，请使用 COLUMN_ENTRY_LENGTH 宏。  
  
- 若要获取状态，请使用 COLUMN_ENTRY_STATUS 宏。  
  
- 若要获取这两项，使用 COLUMN_ENTRY_LENGTH_STATUS，如下所示。  
  
```cpp  
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
  
CTable<CAccessor<CProducts >> product;  
  
product.Open(session, "Product");  

while (product.MoveNext() == S_OK)  
{  
   // Check the product name isn't NULL before tracing it  
   if (product.nNameStatus == DBSTATUS_S_OK)  
      ATLTRACE("%s is %d characters\n", szName, nNameLength);  
}  
```  
  
当你使用`CDynamicAccessor`，长度和状态将为您自动绑定。 若要检索的长度和状态的值，请使用`GetLength`和`GetStatus`成员函数。  
  
## <a name="see-also"></a>请参阅  

[使用 OLE DB 使用者模板](../../data/oledb/working-with-ole-db-consumer-templates.md)