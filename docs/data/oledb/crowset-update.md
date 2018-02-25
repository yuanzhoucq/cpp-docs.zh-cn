---
title: CRowset::Update | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRowset.Update
- ATL.CRowset.Update
- ATL.CRowset<TAccessor>.Update
- ATL::CRowset<TAccessor>::Update
- CRowset<TAccessor>::Update
- CRowset::Update
- CRowset<TAccessor>.Update
- ATL::CRowset::Update
dev_langs:
- C++
helpviewer_keywords:
- Update method
ms.assetid: cd5fedc8-2b85-4cb8-8c40-c79576316903
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5b9acbe5df9d0ccf1a1798f19e41ea9fd1cc0ada
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetupdate"></a>CRowset::Update
传输任何挂起的更改的当前行自从上次提取或**更新**对其调用。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT Update(DBCOUNTITEM* pcRows = NULL,   
   HROW* phRow = NULL,   
   DBROWSTATUS* pStatus = NULL) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `pcRows`  
 [out]指向的位置其中**更新**返回它试图更新，如果所需的行数。  
  
 `phRow`  
 [out]指向的位置其中**更新**返回它尝试更新行的句柄。 如果返回没有句柄`phRow`为 null。  
  
 `pStatus`  
 [out]指向的位置其中**更新**返回的行状态值。 如果返回没有状态`pStatus`为 null。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 传输任何挂起的上次提取或更新该行以来对当前行所做的更改 (使用**更新**或[UpdateAll](../../data/oledb/crowset-updateall.md))。 通常情况下调用[SetData](../../data/oledb/crowset-setdata.md)以在行中的列中设置数据值，然后调用**更新**传输这些更改。  
  
 此方法要求的可选接口`IRowsetUpdate`，这可能不支持对所有提供程序，如果出现这种情况，该方法返回**E_NOINTERFACE**。 你还必须设置**DBPROP_IRowsetUpdate**到`VARIANT_TRUE`之前调用**打开**对表或命令，其中包含行集。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)