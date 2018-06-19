---
title: 'Irowsetchangeimpl:: Setdata |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- SetData
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
dev_langs:
- C++
helpviewer_keywords:
- SetData method
ms.assetid: 81e1dd0a-0518-440c-8808-cee76e4929c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f37ea1e5cbdddf3099356c99acc10014d6ab661f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102207"
---
# <a name="irowsetchangeimplsetdata"></a>IRowsetChangeImpl::SetData
设置一个或多个列中的数据值。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IRowsetChange::SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetChangeImpl 类](../../data/oledb/irowsetchangeimpl-class.md)