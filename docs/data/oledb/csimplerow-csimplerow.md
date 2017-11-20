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
ms.openlocfilehash: 0cd8371f1a44cb26812f6bc03e2394095447cc8b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [CSimpleRow 类](../../data/oledb/csimplerow-class.md)