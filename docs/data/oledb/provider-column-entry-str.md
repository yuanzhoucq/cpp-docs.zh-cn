---
title: PROVIDER_COLUMN_ENTRY_STR |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY_STR
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_STR macro
ms.assetid: f1c27dd6-9ab8-4821-8685-d4dd15e76e88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9ede31951c916c8b70b4942c3077442b5e2e3313
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104615"
---
# <a name="providercolumnentrystr"></a>PROVIDER_COLUMN_ENTRY_STR
表示提供程序支持的特定列。  
  
## <a name="syntax"></a>语法  
  
```cpp
PROVIDER_COLUMN_ENTRY_STR(name  
, ordinal, member )  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
 [in]列名称。  
  
 `ordinal`  
 [in] 列号。 除非列是书签列，列数必须不为 0。  
  
 `member`  
 [in]将数据存储的数据类中的成员变量。  
  
## <a name="remarks"></a>备注  
 使用此宏时列数据被假定为[DBTYPE_STR](https://msdn.microsoft.com/en-us/library/ms711251.aspx)。  
  
## <a name="example"></a>示例  
 请参阅[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)