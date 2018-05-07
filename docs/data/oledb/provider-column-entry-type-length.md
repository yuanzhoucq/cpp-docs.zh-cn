---
title: PROVIDER_COLUMN_ENTRY_TYPE_LENGTH |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
ms.assetid: a60b1a8b-0903-4ff4-91ec-ed62126449fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ef9af591bff5a13a5780cc27ef169a8447c64cc7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="providercolumnentrytypelength"></a>PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
表示提供程序支持的特定列。  
  
## <a name="syntax"></a>语法  
  
```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name  
, ordinal, dbtype, size, member )  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
  
 [in]列名称。  
  
 `ordinal`  
 [in] 列号。 除非列是书签列，列数必须不为 0。  
  
 `dbtype`  
 [in]中的数据类型[DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx)。  
  
 `size`  
 [in]列大小 （字节）。  
  
 `member`  
 [in]将数据存储的数据类中的成员变量。  
  
## <a name="remarks"></a>备注  
 类似于[PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md)但还可以指定列的数据类型，以及大小。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)