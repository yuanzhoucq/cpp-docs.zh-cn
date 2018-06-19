---
title: 'Crowset:: Setdata |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CRowset<TAccessor>.SetData
- SetData
- ATL::CRowset::SetData
- CRowset<TAccessor>.SetData
- CRowset::SetData
- ATL.CRowset.SetData
- CRowset.SetData
- CRowset<TAccessor>::SetData
- ATL::CRowset<TAccessor>::SetData
dev_langs:
- C++
helpviewer_keywords:
- SetData method
ms.assetid: 68125142-8510-4132-9393-e39efd39c784
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b8885c6e64fa7e7e22f6858d916a8e1afa8738d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098467"
---
# <a name="crowsetsetdata"></a>CRowset::SetData
设置行的一个或多个列中的数据值。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT SetData() const throw();   


HRESULT SetData(int nAccessor) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 `nAccessor`  
 [in]访问器可用于访问数据的数。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 有关`SetData`用于接受任何参数，所有访问器的窗体更新。 通常情况下调用**SetData**在行中的列中设置数据值，然后调用[更新](../../data/oledb/crowset-update.md)传输这些更改。  
  
 此方法要求的可选接口`IRowsetChange`，这可能不支持对所有提供程序，如果出现这种情况，该方法返回**E_NOINTERFACE**。 你还必须设置**DBPROP_IRowsetChange**到`VARIANT_TRUE`之前调用**打开**对表或命令，其中包含行集。  
  
 如果一个或多个列是不可写，设置操作可能会失败。 修改光标映射以更正此问题。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [CRowset::Update](../../data/oledb/crowset-update.md)