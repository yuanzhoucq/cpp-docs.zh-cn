---
title: "CSchemata，CSchemataInfo |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- DEFAULT_CHARACTER_SET_CATALOG
- DEFAULT_CHARACTER_SET_SCHEMA
- m_szCharName
- CSchemataInfo
- m_szCatalog
- m_szCharCatalog
- m_szOwner
- m_szCharSchema
- CSchemata
- m_szName
- DEFAULT_CHARACTER_SET_NAME
dev_langs:
- C++
helpviewer_keywords:
- m_szCharName
- CSchemata typedef class
- DEFAULT_CHARACTER_SET_NAME
- m_szOwner
- CSchemataInfo parameter class
- DEFAULT_CHARACTER_SET_CATALOG
- m_szCharSchema
- m_szCatalog
- m_szName
- m_szCharCatalog
- DEFAULT_CHARACTER_SET_SCHEMA
ms.assetid: 9d06d65a-c27b-446d-bc42-c7e487b0d9c5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c5bcd0477fe2285f5009aeb04c871f72c564365e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cschemata-cschematainfo"></a>CSchemata，CSchemataInfo
调用 typedef 类**CSchemata**来实现其参数类**CSchemataInfo**。  
  
## <a name="remarks"></a>备注  
 请参阅[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)有关使用 typedef 类的详细信息。  
  
 此类标识给定用户拥有的架构。  
  
 下表列出了类数据成员及其对应的 OLE DB 列。 请参阅[架构行集](https://msdn.microsoft.com/en-us/library/ms716887.aspx)中*OLE DB 程序员参考*有关的架构和列的详细信息。  
  
|数据成员|OLE DB 列|  
|------------------|--------------------|  
|m_szCatalog|CATALOG_NAME|  
|m_szName|SCHEMA_NAME|  
|m_szOwner|SCHEMA_OWNER|  
|m_szCharCatalog|DEFAULT_CHARACTER_SET_CATALOG|  
|m_szCharSchema|DEFAULT_CHARACTER_SET_SCHEMA|  
|m_szCharName|DEFAULT_CHARACTER_SET_NAME|  
  
## <a name="requirements"></a>惠?  
 **标头：** atldbsch.h  
  
## <a name="see-also"></a>请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)