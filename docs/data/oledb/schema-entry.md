---
title: SCHEMA_ENTRY |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- SCHEMA_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- SCHEMA_ENTRY macro
ms.assetid: e8bee479-80f3-417e-8f41-cdaddd49690c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 665b337861959b28670a0b2e57649814853a7384
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33109516"
---
# <a name="schemaentry"></a>SCHEMA_ENTRY
将 GUID 与类相关联。  
  
## <a name="syntax"></a>语法  
  
```cpp
      SCHEMA_ENTRY(guid,  
   rowsetClass);   
```  
  
#### <a name="parameters"></a>参数  
 `guid`  
 架构行集 GUID。 请参阅[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)中*OLE DB 程序员参考*有关架构行集和其 Guid 的列表。  
  
 *rowsetClass*  
 将创建来表示架构行集类。  
  
## <a name="remarks"></a>备注  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)然后，可以查询有关的 Guid，列表映射或如果它有一个 GUID，它可以创建一个行集。 架构行集`IDBSchemaRowsetImpl`创建类似于标准`CRowsetImpl`-派生类，但它必须提供**执行**具有以下签名的方法：  
  
```  
HRESULT Execute (LONG* pcRowsAffected,  
    ULONG cRestrictions,  
    const VARIANT* rgRestrictions);  
```  
  
 这**执行**函数填充行集的数据。 ATL 项目向导创建中, 所述[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)中*OLE DB 程序员参考*，三个初始的三个必需的 OLE DB 架构的每个项目中的架构行集：  
  
-   `DBSCHEMA_TABLES`  
  
-   **DBSCHEMA_COLUMNS**  
  
-   **DBSCHEMA_PROVIDER_TYPES**  
  
 向导还会在架构映射中添加三个对应的条目。 请参阅[创建 OLE DB 模板提供程序](../../data/oledb/creating-an-ole-db-provider.md)有关使用向导创建提供程序的详细信息。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [BEGIN_SCHEMA_MAP](../../data/oledb/begin-schema-map.md)   
 [END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)