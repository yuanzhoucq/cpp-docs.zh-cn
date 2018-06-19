---
title: 'Irowsetcreatorimpl:: Setsite |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
dev_langs:
- C++
helpviewer_keywords:
- SetSite method
ms.assetid: e92e63d5-93e4-4ee0-9ef7-bb6583cc8091
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: af2883b261b754cee04e2c5090d1ef9b9887c04f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101378"
---
# <a name="irowsetcreatorimplsetsite"></a>IRowsetCreatorImpl::SetSite
设置包含行集对象的站点。 有关详细信息，请参阅[IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869)。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(SetSite )(IUnknown* pCreator);  
```  
  
#### <a name="parameters"></a>参数  
 `pCreator`  
 [in]指向**IUnknown**管理行集对象的站点的接口指针。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此外，`IRowsetCreatorImpl::SetSite`使 OLE DB **DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS**属性。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetCreatorImpl 类](../../data/oledb/irowsetcreatorimpl-class.md)