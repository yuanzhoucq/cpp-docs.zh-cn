---
title: "Crowset:: Issamerow |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowset::IsSameRow
- CRowset.IsSameRow
- IsSameRow
- ATL::CRowset::IsSameRow
- ATL.CRowset.IsSameRow
- CRowset<TAccessor>::IsSameRow
- ATL.CRowset<TAccessor>.IsSameRow
- CRowset<TAccessor>.IsSameRow
- ATL::CRowset<TAccessor>::IsSameRow
dev_langs: C++
helpviewer_keywords: IsSameRow method
ms.assetid: 53cba847-52f5-4dd9-973f-bbe7454c425c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a67952947275789fbcb38e8807a2b754cd4baf8a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetissamerow"></a>CRowset::IsSameRow
将具有当前行的指定的行进行比较。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT IsSameRow(   
   HROW hRow    
) const throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `hRow`  
 [in]要与当前行进行比较的行句柄。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。 `S_OK`指示行相同。 其他值，请参阅[IRowsetIndentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx)中*OLE DB 程序员参考*Windows SDK 中。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>另请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)