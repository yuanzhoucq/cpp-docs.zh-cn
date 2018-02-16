---
title: "Csimplerow:: Csimplerow |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 626044d5fec50c41b79867eb775ba913fd6c03ca
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
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
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [CSimpleRow 类](../../data/oledb/csimplerow-class.md)