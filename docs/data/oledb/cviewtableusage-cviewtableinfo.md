---
title: "CViewTableUsage，CViewTableInfo |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- m_szTableSchema
- m_szCatalog
- CViewTableInfo
- m_szTableCatalog
- m_szSchema
- m_szTableName
- m_szName
- CViewTableUsage
dev_langs: C++
helpviewer_keywords:
- CViewTableInfo parameter class
- CViewTableUsage typedef class
- m_szSchema
- m_szTableSchema
- TABLE_CATALOG
- m_szCatalog
- TABLE_NAME
- TABLE_SCHEMA
- m_szName
- m_szTableCatalog
- m_szTableName
ms.assetid: 10b74f2a-8010-4f97-acc2-ffce07349981
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8356034c9111740ccc6039514c4b8a3766089221
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cviewtableusage-cviewtableinfo"></a>CViewTableUsage，CViewTableInfo
调用 typedef 类**CViewTableUsage**来实现其参数类**CViewTableInfo**。  
  
## <a name="remarks"></a>备注  
 请参阅[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)有关使用 typedef 类的详细信息。  
  
 此类标识查看定义的表，在目录中，可以访问给定的用户。  
  
 下表列出了类数据成员及其对应的 OLE DB 列。 请参阅[VIEW_TABLE_USAGE 行集](https://msdn.microsoft.com/en-us/library/ms719727.aspx)中*OLE DB 程序员参考*有关的架构和列的详细信息。  
  
|数据成员|OLE DB 列|  
|------------------|--------------------|  
|m_szCatalog|VIEW_CATALOG|  
|m_szSchema|VIEW_SCHEMA|  
|m_szName|VIEW_NAME|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
  
## <a name="requirements"></a>要求  
 **标头：** atldbsch.h  
  
## <a name="see-also"></a>另请参阅  
 [CRestrictions 类](../../data/oledb/crestrictions-class.md)