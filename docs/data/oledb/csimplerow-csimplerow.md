---
title: 'Csimplerow:: Csimplerow |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow::CSimpleRow
- CSimpleRow.CSimpleRow
- ATL.CSimpleRow.CSimpleRow
- CSimpleRow::CSimpleRow
dev_langs:
- C++
helpviewer_keywords:
- CSimpleRow class, constructor
ms.assetid: 3968a36c-b8bb-48df-bd06-3956e64b0842
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 28033bb7fd8d0bd60fdea9fa4d12691ef87ef57d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="csimplerowcsimplerow"></a>CSimpleRow::CSimpleRow
构造函数。  
  
## <a name="syntax"></a>语法  
  
```cpp
      CSimpleRow(DBCOUNTITEM iRowsetCur);  
```  
  
#### <a name="parameters"></a>参数  
 `iRowsetCur`  
 [in]当前行集的索引。  
  
## <a name="remarks"></a>备注  
 集[m_iRowset](../../data/oledb/csimplerow-m-irowset.md)到`iRowsetCur`。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [CSimpleRow 类](../../data/oledb/csimplerow-class.md)