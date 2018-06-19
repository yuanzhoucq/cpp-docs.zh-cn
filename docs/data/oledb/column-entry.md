---
title: COLUMN_ENTRY |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY macro
ms.assetid: a10aef29-6d70-49ec-b572-5b5c4abe1b46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1d2f1466b660d3235f3fffe5b7eed9aa80696d7c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091140"
---
# <a name="columnentry"></a>COLUMN_ENTRY
在行集中的特定列表示行集上的绑定。  
  
## <a name="syntax"></a>语法  
  
```cpp
COLUMN_ENTRY(nOrdinal, data)  
  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)中*OLE DB 程序员参考*。  
  
 `nOrdinal`  
 [in] 列号。  
  
 `data`  
 [in] 用户记录中的对应数据成员。  
  
## <a name="remarks"></a>备注  
 `COLUMN_ENTRY`在下列位置使用宏：  
  
-   之间[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏。  
  
-   之间[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。  
  
-   之间[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏。  
  
## <a name="example"></a>示例  
 请参阅中的宏主题中，示例[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数 OLE DB 使用者模板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)   
 [COLUMN_ENTRY_PS](../../data/oledb/column-entry-ps.md)   
 [COLUMN_ENTRY_PS_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN_ENTRY_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN_ENTRY_LENGTH_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN_ENTRY_PS_LENGTH_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN_ENTRY_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN_ENTRY_PS_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [COLUMN_ENTRY_TYPE](../../data/oledb/column-entry-type.md)   
 [COLUMN_ENTRY_TYPE_SIZE](../../data/oledb/column-entry-type-size.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)