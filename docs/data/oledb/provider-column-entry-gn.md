---
title: PROVIDER_COLUMN_ENTRY_GN |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY_GN
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_GN macro
ms.assetid: be77ba85-634c-4e28-832f-d2fa40413254
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: be0cfa80b0d2a18d04dd329feda6547b5d89e6e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="providercolumnentrygn"></a>PROVIDER_COLUMN_ENTRY_GN
表示提供程序支持的特定列。  
  
## <a name="syntax"></a>语法  
  
```cpp
PROVIDER_COLUMN_ENTRY_GN (name  
, ordinal, flags, colSize, dbtype, precision, scale, guid )  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
 [in]列名称。  
  
 `ordinal`  
 [in] 列号。 除非列是书签列，列数必须不为 0。  
  
 `flags`  
 [in]指定返回数据的方式。 请参阅`dwFlags`中的说明[DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 *colSize*  
 [in]列大小中。  
  
 `dbtype`  
 [in]指示值的数据类型。 请参阅**wType**中的说明[DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 *precision*  
 [in]指示如果获取数据时要使用的精度*dbType*是`DBTYPE_NUMERIC`或**DBTYPE_DECIMAL**。 请参阅**bPrecision**中的说明[DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 `scale`  
 [in]指示要使用的 dbType 是否获取数据时的比例`DBTYPE_NUMERIC`或**DBTYPE_DECIMAL**。 请参阅**bScale**中的说明[DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 `guid`  
 架构行集 GUID。 请参阅[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)中*OLE DB 程序员参考*有关架构行集和其 Guid 的列表。  
  
## <a name="remarks"></a>备注  
 使用此选项可以指定列的大小、 数据类型、 精度、 小数位数和架构行集 GUID。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)