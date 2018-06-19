---
title: 'Irowsetlocateimpl:: Getrowsbybookmark |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetLocateImpl::GetRowsByBookmark
- IRowsetLocateImpl.GetRowsByBookmark
- GetRowsByBookmark
dev_langs:
- C++
helpviewer_keywords:
- GetRowsByBookmark method
ms.assetid: 07906e42-3582-427e-812a-aa19791e3c56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 84bfc1333729b9ed097f50ae98fca997b45e7da5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103588"
---
# <a name="irowsetlocateimplgetrowsbybookmark"></a>IRowsetLocateImpl::GetRowsByBookmark
获取一个或多个匹配指定的书签的行。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD (GetRowsByBookmark )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const DBBKMARK rgcbBookmarks[],  
   const BYTE* rgpBookmarks,  
   HROW rghRows[],  
   DBROWSTATUS* rgRowStatus[]);  
```  
  
#### <a name="parameters"></a>参数  
 `hReserved`  
 [in]对应于`hChapter`参数[IRowsetLocate::GetRowsByBookmark](https://msdn.microsoft.com/en-us/library/ms725420.aspx)。  
  
 其他参数，请参阅[IRowsetLocate::GetRowsByBookmark](https://msdn.microsoft.com/en-us/library/ms725420.aspx)中*OLE DB 程序员参考*。  
  
## <a name="remarks"></a>备注  
 书签可以为你定义的值或 OLE DB[标准书签](https://msdn.microsoft.com/en-us/library/ms712954.aspx)(**DBBMK_FIRST**或**DBBMK_LAST**)。 不会更改光标位置。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetLocateImpl 类](../../data/oledb/irowsetlocateimpl-class.md)   
 [IRowsetLocateImpl::GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)