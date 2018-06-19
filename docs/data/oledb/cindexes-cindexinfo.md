---
title: CIndexes，CIndexInfo |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- INITIAL_SIZE
- NULL_COLLATION
- m_szFilterCondition
- m_bPrimaryKey
- m_szTableSchema
- m_bSortBookmarks
- m_szIndexSchema
- m_nColumnPropID
- ORDINAL_POSITION
- INDEX_CATALOG
- m_nOrdinalPosition
- COLUMN_GUID
- m_bAutoUpdate
- m_nNullCollation
- CLUSTERED
- NULLS
- m_szColumnName
- m_nFillFactor
- m_nPages
- INDEX_NAME
- m_szTableCatalog
- m_szIndexName
- m_szIndexCatalog
- m_nCardinality
- m_nInitialSize
- m_bUnique
- COLUMN_PROPID
- m_guidColumn
- m_nNulls
- m_szTableName
- FILL_FACTOR
- m_nType
- m_bClustered
- COLLATION
- FILTER_CONDITION
- m_nCollation
- CIndexes
- INDEX_SCHEMA
- CIndexInfo
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_PROPID
- ORDINAL_POSITION
- INDEX_CATALOG
- NULLS
- CIndexInfo parameter class
- m_szFilterCondition
- m_szIndexCatalog
- CLUSTERED
- m_nType
- FILL_FACTOR
- m_nPages
- m_nCardinality
- m_szTableSchema
- TABLE_CATALOG
- TABLE_NAME
- INDEX_SCHEMA
- m_nInitialSize
- m_nOrdinalPosition
- m_nColumnPropID
- FILTER_CONDITION
- TABLE_SCHEMA
- m_szColumnName
- INDEX_NAME
- NULL_COLLATION
- m_bUnique
- m_bSortBookmarks
- m_bAutoUpdate
- COLUMN_NAME
- INITIAL_SIZE
- m_szTableCatalog
- m_nNullCollation
- m_bClustered
- m_szTableName
- CIndexes typedef class
- m_nCollation
- COLUMN_GUID
- m_guidColumn
- m_nNulls
- m_bPrimaryKey
- m_szIndexName
- m_nFillFactor
- m_szIndexSchema
ms.assetid: 592fa773-fd23-4332-8d47-d76101f9ddd7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3e924defd8645f72277bb9fa89eb5827e67c07c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098701"
---
# <a name="cindexes-cindexinfo"></a>CIndexes，CIndexInfo
调用 typedef 类**CIndexes**来实现其参数类**CIndexInfo**。  
  
## <a name="remarks"></a>备注  
 请参阅[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)有关使用 typedef 类的详细信息。  
  
 此类标识定义的索引，在目录中，属于给定用户。  
  
 下表列出了类数据成员及其对应的 OLE DB 列。 请参阅[索引行集](https://msdn.microsoft.com/en-us/library/ms709712.aspx)中*OLE DB 程序员参考*有关的架构和列的详细信息。  
  
|数据成员|OLE DB 列|  
|------------------|--------------------|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
|m_szIndexCatalog|INDEX_CATALOG|  
|m_szIndexSchema|INDEX_SCHEMA|  
|m_szIndexName|INDEX_NAME|  
|m_bPrimaryKey|PRIMARY_KEY|  
|m_bUnique|UNIQUE|  
|m_bClustered|CLUSTERED|  
|m_nType|TYPE|  
|m_nFillFactor|FILL_FACTOR|  
|m_nInitialSize|INITIAL_SIZE|  
|m_nNulls|NULLS|  
|m_bSortBookmarks|SORT_BOOKMARKS|  
|m_bAutoUpdate|AUTO_UPDATE|  
|m_nNullCollation|NULL_COLLATION|  
|m_nOrdinalPosition|ORDINAL_POSITION|  
|m_szColumnName|COLUMN_NAME|  
|m_guidColumn|COLUMN_GUID|  
|m_nColumnPropID|COLUMN_PROPID|  
|m_nCollation|COLLATION|  
|m_nCardinality|CARDINALITY|  
|m_nPages|PAGES|  
|m_szFilterCondition|FILTER_CONDITION|  
  
## <a name="requirements"></a>要求  
 **标头：** atldbsch.h  
  
## <a name="see-also"></a>请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)