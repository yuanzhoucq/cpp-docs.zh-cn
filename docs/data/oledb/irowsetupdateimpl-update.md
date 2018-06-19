---
title: 'Irowsetupdateimpl:: Update |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
dev_langs:
- C++
helpviewer_keywords:
- Update method
ms.assetid: 9ec6884d-aa9c-4871-a803-c048f162403c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c47ee5bf8c8ddc3436414e89b7d365c06158f195
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104238"
---
# <a name="irowsetupdateimplupdate"></a>IRowsetUpdateImpl::Update
传输自上次提取或更新后对行进行任何更改。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD (Update )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>参数  
 `hReserved`  
 [in]对应于`hChapter`中的参数[IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)。  
  
 其他参数，请参阅[IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)中*OLE DB 程序员参考*。  
  
## <a name="remarks"></a>备注  
 通过调用传输更改[irowsetchangeimpl:: Flushdata](../../data/oledb/irowsetchangeimpl-flushdata.md)。 使用者必须调用[crowset:: Update](../../data/oledb/crowset-update.md)以使更改生效。 设置*prgRowstatus*为适当的值中所述[行状态](https://msdn.microsoft.com/en-us/library/ms722752.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)