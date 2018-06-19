---
title: COLUMN_ENTRY_LENGTH_STATUS |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_LENGTH_STATUS
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY_LENGTH_STATUS macro
ms.assetid: 6069967c-4665-462b-b822-1e6c22b5bee1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 90f05219da4382f759934e39c074bc6cb81817a7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097804"
---
# <a name="columnentrylengthstatus"></a>COLUMN_ENTRY_LENGTH_STATUS
表示行集上与数据库中的特定列的绑定。  
  
## <a name="syntax"></a>语法  
  
```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)  
  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)中*OLE DB 程序员参考*。  
  
 `nOrdinal`  
 [in] 列号。  
  
 `data`  
 [in] 用户记录中的对应数据成员。  
  
 *length*  
 [in] 要绑定到列长度的变量。  
  
 *status*  
 [in] 要绑定到列变量的状态。  
  
## <a name="remarks"></a>备注  
 当您要支持长度和状态变量时，请使用此宏。 它在以下位置中使用：  
  
-   之间[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏。  
  
-   之间[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。  
  
-   之间[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数 OLE DB 使用者模板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)   
 [COLUMN_ENTRY_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN_ENTRY_PS](../../data/oledb/column-entry-ps.md)   
 [COLUMN_ENTRY_PS_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN_ENTRY_PS_LENGTH_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN_ENTRY_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN_ENTRY_PS_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)