---
title: CAssertions，CAssertionInfo |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAssertions
- m_szCatalog
- m_bInitiallyDeferred
- CONSTRAINT_NAME
- m_szSchema
- INITIALLY_DEFERRED
- m_bIsDeferrable
- m_szName
- CAssertionInfo
- CONSTRAINT_CATALOG
- CONSTRAINT_SCHEMA
- IS_DEFERRABLE
dev_langs:
- C++
helpviewer_keywords:
- CAssertionInfo parameter class
- DESCRIPTION class data member
- CAssertions typedef class
- IS_DEFERRABLE
- m_szSchema
- m_bInitiallyDeferred
- CONSTRAINT_CATALOG
- m_szCatalog
- CONSTRAINT_NAME
- CONSTRAINT_SCHEMA
- m_szName
- m_szDescription
- INITIALLY_DEFERRED
- m_bIsDeferrable
ms.assetid: 2a79c2da-5c9b-4fa6-98e8-90b7f5d6f021
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6b3a114d4df8effe682798c966811be0eacc41e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094425"
---
# <a name="cassertions-cassertioninfo"></a>CAssertions，CAssertionInfo
调用 typedef 类**CAssertions**来实现其参数类**CAssertionInfo**。  
  
## <a name="remarks"></a>备注  
 请参阅[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)有关使用 typedef 类的详细信息。  
  
 此类标识的目录中定义由给定用户所拥有的断言。  
  
 下表列出了类数据成员的**CAssertionInfo**和其对应的 OLE DB 列。 请参阅[断言行集](https://msdn.microsoft.com/en-us/library/ms719776.aspx)中*OLE DB 程序员参考*有关的架构和列的详细信息。  
  
|数据成员|OLE DB 列|  
|------------------|--------------------|  
|m_szCatalog|CONSTRAINT_CATALOG|  
|m_szSchema|CONSTRAINT_SCHEMA|  
|m_szName|CONSTRAINT_NAME|  
|m_bIsDeferrable|IS_DEFERRABLE|  
|m_bInitiallyDeferred|INITIALLY_DEFERRED|  
|m_szDescription|说明|  
  
## <a name="requirements"></a>要求  
 **标头：** atldbsch.h  
  
## <a name="see-also"></a>请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)