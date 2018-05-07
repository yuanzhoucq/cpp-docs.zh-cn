---
title: 'Caccessorbase:: Releaseaccessors |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAccessorBase::ReleaseAccessors
- CAccessorBase.ReleaseAccessors
- ReleaseAccessors
dev_langs:
- C++
helpviewer_keywords:
- ReleaseAccessors method
ms.assetid: f08bc88e-0552-4a9c-9c65-b4061094649a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1c73035e27b1f896891630cd9b4d9a135b3c4758
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="caccessorbasereleaseaccessors"></a>CAccessorBase::ReleaseAccessors
释放类创建的访问器。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);  
```  
  
#### <a name="parameters"></a>参数  
 *pUnk*  
 [in]指向的指针**IUnknown** COM 对象为其创建访问器的接口。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 从调用[caccessorrowset:: Close](../../data/oledb/caccessorrowset-close.md)。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CAccessorBase 类](../../data/oledb/caccessorbase-class.md)