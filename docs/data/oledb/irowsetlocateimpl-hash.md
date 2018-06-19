---
title: 'Irowsetlocateimpl:: Hash |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetLocateImpl::Hash
- IRowsetLocateImpl.Hash
dev_langs:
- C++
helpviewer_keywords:
- Hash method
ms.assetid: 7df4386d-80fb-4332-a85f-baae98cdc6e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 42076453cc8f32b56bfe354eaa2b883650d0f4f7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101183"
---
# <a name="irowsetlocateimplhash"></a>IRowsetLocateImpl::Hash
返回哈希值用于指定书签。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD (Hash )(HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmarks,  
   const DBBKMARK* rgcbBookmarks[],  
   const BYTE* rgpBookmarks[],  
   DBHASHVALUE rgHashValues[],  
   DBROWSTATUS rgBookmarkStatus[]);  
```  
  
#### <a name="parameters"></a>参数  
 `hReserved`  
 [in]对应于`hChapter`参数[IRowsetLocate::Hash](https://msdn.microsoft.com/en-us/library/ms709697.aspx)。  
  
 其他参数，请参阅[IRowsetLocate::Hash](https://msdn.microsoft.com/en-us/library/ms709697.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetLocateImpl 类](../../data/oledb/irowsetlocateimpl-class.md)