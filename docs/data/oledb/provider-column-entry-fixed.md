---
title: PROVIDER_COLUMN_ENTRY_FIXED |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY_FIXED
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_FIXED macro
ms.assetid: 71f9c9aa-56a0-488b-96ba-5c72da9c71d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 901a5ba5e903af95d846c21cca297387f1aaf57e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104979"
---
# <a name="providercolumnentryfixed"></a>PROVIDER_COLUMN_ENTRY_FIXED
表示提供程序支持的特定列。  
  
## <a name="syntax"></a>语法  
  
```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name  
, ordinal, dbtype, member )  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
 [in]列名称。  
  
 `ordinal`  
 [in] 列号。 除非列是书签列，列数必须不为 0。  
  
 `dbtype`  
 [in]中的数据类型[DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx)。  
  
 `member`  
 [in]中的成员变量`dataClass`中存储该数据。  
  
## <a name="remarks"></a>备注  
 允许你指定的列数据类型。  
  
## <a name="example"></a>示例  
 请参阅[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)