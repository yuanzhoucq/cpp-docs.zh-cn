---
title: CStatistics，CStatisticInfo |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CStatistics
- m_szTableSchema
- CStatisticInfo
- m_szTableCatalog
- m_nCardinality
- m_szTableName
dev_langs:
- C++
helpviewer_keywords:
- m_nCardinality
- m_szTableSchema
- TABLE_CATALOG
- TABLE_NAME
- TABLE_SCHEMA
- CStatistics typedef class
- m_szTableCatalog
- m_szTableName
- CStatisticInfo parameter class
ms.assetid: 5822231c-6963-44a6-ae2f-29aca76e1600
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9ad61624077eb1c02337fdd4737853522533a8a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101492"
---
# <a name="cstatistics-cstatisticinfo"></a>CStatistics，CStatisticInfo
调用 typedef 类**CStatistics**来实现其参数类**CStatisticInfo**。  
  
## <a name="remarks"></a>备注  
 请参阅[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)有关使用 typedef 类的详细信息。  
  
 此类标识的统计信息，定义在目录中，由给定用户所拥有。  
  
 下表列出了类数据成员及其对应的 OLE DB 列。 请参阅[统计信息行集](https://msdn.microsoft.com/en-us/library/ms715957.aspx)中*OLE DB 程序员参考*有关的架构和列的详细信息。  
  
|数据成员|OLE DB 列|  
|------------------|--------------------|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
|m_nCardinality|CARDINALITY|  
  
## <a name="requirements"></a>要求  
 **标头：** atldbsch.h  
  
## <a name="see-also"></a>请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)