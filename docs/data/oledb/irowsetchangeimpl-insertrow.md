---
title: 'Irowsetchangeimpl:: Insertrow |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
dev_langs:
- C++
helpviewer_keywords:
- InsertRow method
ms.assetid: 93027be3-921e-438e-a19a-6e5aadb813eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7d8a03489e2754b6b35873cad9c6db245e1f01a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101807"
---
# <a name="irowsetchangeimplinsertrow"></a>IRowsetChangeImpl::InsertRow
创建并初始化新行集中的行。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,  
   HACCESSOR hAccessor,  
   void* pData,  
   HROW* phRow);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IRowsetChange::InsertRow](https://msdn.microsoft.com/en-us/library/ms716921.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetChangeImpl 类](../../data/oledb/irowsetchangeimpl-class.md)