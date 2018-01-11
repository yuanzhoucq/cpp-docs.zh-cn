---
title: "Csimplerow:: Csimplerow |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow::CSimpleRow
- CSimpleRow.CSimpleRow
- ATL.CSimpleRow.CSimpleRow
- CSimpleRow::CSimpleRow
dev_langs: C++
helpviewer_keywords: CSimpleRow class, constructor
ms.assetid: 3968a36c-b8bb-48df-bd06-3956e64b0842
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aaf96092efa8e3e595e815fddd5b0d3a75260702
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="csimplerowcsimplerow"></a>CSimpleRow::CSimpleRow
构造函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
      CSimpleRow(  
   DBCOUNTITEM iRowsetCur   
);  
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