---
title: 'Irowsetupdateimpl:: Isupdateallowed |Microsoft 文档'
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
dev_langs:
- C++
helpviewer_keywords:
- IsUpdateAllowed method
ms.assetid: d6daf3b3-a8e0-4275-a67d-897dea01e297
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 363626cedddea3da57e829a43c21c63b5c2b05cd
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121999"
---
# <a name="irowsetupdateimplisupdateallowed"></a>IRowsetUpdateImpl::IsUpdateAllowed
重写此方法来检查安全性，完整性，在更新之前，依此类推。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,  
   HROW /* [in] */ /* hRowUpdate */,  
   DBROWSTATUS* /* [out] */ /* pRowStatus */);  
```  
  
#### <a name="parameters"></a>参数  
 *status*  
 [in]挂起的操作的行的状态。  
  
 *hRowUpdate*  
 [in]用户想要更新的行的句柄。  
  
 *pRowStatus*  
 [out]向用户返回的状态。  
  
## <a name="remarks"></a>备注  
 如果你确定应允许更新，则返回`S_OK`; 否则返回**E_FAIL**。 如果你允许更新，还需要设置**DBROWSTATUS**中[irowsetupdateimpl:: Update](../../data/oledb/irowsetupdateimpl-update.md)给适当[行状态](https://msdn.microsoft.com/en-us/library/ms722752.aspx)。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)