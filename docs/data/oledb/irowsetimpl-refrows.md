---
title: "Irowsetimpl:: Refrows |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
dev_langs: C++
helpviewer_keywords: RefRows method
ms.assetid: 1c048a2a-65dc-4bba-9c81-a23c0dc249c8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1ace41e40b1a6d8a08060288209d3d2b60a626fa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetimplrefrows"></a>IRowsetImpl::RefRows
由调用[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)和[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)递增或释放到一个现有的行句柄的引用计数。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT RefRows(  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[],  
   BOOL bAdd   
);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[irowset:: Addrefrows](https://msdn.microsoft.com/en-us/library/ms719619.aspx)中*OLE DB 程序员参考*。  
  
## <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)   
 [CSimpleRow 类](../../data/oledb/csimplerow-class.md)