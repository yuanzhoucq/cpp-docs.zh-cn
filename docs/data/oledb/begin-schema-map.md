---
title: "BEGIN_SCHEMA_MAP |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BEGIN_SCHEMA_MAP
dev_langs: C++
helpviewer_keywords: BEGIN_SCHEMA_MAP macro
ms.assetid: 4e751023-35bc-4efd-9018-5448dd1ad751
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9682ac8a31ec7c585b1da7b9bc14388413ba56fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="beginschemamap"></a>BEGIN_SCHEMA_MAP
表示架构映射的开头。  
  
## <a name="syntax"></a>语法  
  
```  
  
      BEGIN_SCHEMA_MAP(  
   SchemaClass   
);  
```  
  
#### <a name="parameters"></a>参数  
 *SchemaClass*  
 包含地图的类。 通常，这将是会话类。  
  
## <a name="remarks"></a>备注  
 请参阅[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)有关架构行集的详细信息的 Windows SDK 中。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)   
 [END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)   
 [IDBSchemaRowsetImpl 类](../../data/oledb/idbschemarowsetimpl-class.md)