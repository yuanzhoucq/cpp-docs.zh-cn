---
title: 'Crowset:: Getrowstatus |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset.GetRowStatus
- ATL.CRowset<TAccessor>.GetRowStatus
- ATL::CRowset<TAccessor>::GetRowStatus
- CRowset::GetRowStatus
- ATL::CRowset::GetRowStatus
- CRowset<TAccessor>::GetRowStatus
- ATL.CRowset.GetRowStatus
- CRowset<TAccessor>.GetRowStatus
- GetRowStatus
dev_langs:
- C++
helpviewer_keywords:
- GetRowStatus method
ms.assetid: 7a29a235-cb7e-40c1-92ce-5441751febee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3e3a0fb71a06a407a80a98717af53da926436f57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetgetrowstatus"></a>CRowset::GetRowStatus
返回所有行的状态。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetRowStatus(DBPENDINGSTATUS* pStatus) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 `pStatus`  
 [out]指向一个位置的指针其中`GetRowStatus`返回的状态值。 请参阅 OLE DB 程序员参考中的 DBPENDINGSTATUS。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此方法要求的可选接口`IRowsetUpdate`，这可能不支持对所有提供程序，如果出现这种情况，该方法返回**E_NOINTERFACE**。 你还必须设置**DBPROP_IRowsetUpdate**到`VARIANT_TRUE`之前调用**打开**对表或命令，其中包含行集。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/en-us/library/ms724377.aspx)