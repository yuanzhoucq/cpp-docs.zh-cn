---
title: COLUMN_ENTRY_TYPE_SIZE |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_TYPE_SIZE
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY_TYPE_SIZE macro
ms.assetid: d8b169e8-af22-464b-8cb3-eaa346f7a739
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1acb969015acda4213532cac3e185bf97a3ac31d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="columnentrytypesize"></a>COLUMN_ENTRY_TYPE_SIZE
表示数据库中的特定列的绑定。 支持`type`和`size`参数。  
  
## <a name="syntax"></a>语法  
  
```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)  
  
```  
  
#### <a name="parameters"></a>参数  
 `nOrdinal`  
 [in] 列号。  
  
 `wType`  
 [in]数据类型列条目。  
  
 `nLength`  
 [in]以字节为单位的列项的大小。  
  
 `data`  
 [in] 用户记录中的对应数据成员。  
  
## <a name="remarks"></a>备注  
 此宏是专用的变体[COLUMN_ENTRY](../../data/oledb/column-entry.md)提供了一种指定数据大小和类型的宏。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数 OLE DB 使用者模板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)