---
title: "Crowset:: Updateall |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowset::UpdateAll
- ATL.CRowset.UpdateAll
- CRowset<TAccessor>.UpdateAll
- ATL.CRowset<TAccessor>.UpdateAll
- UpdateAll
- CRowset.UpdateAll
- ATL::CRowset<TAccessor>::UpdateAll
- CRowset<TAccessor>::UpdateAll
- ATL::CRowset::UpdateAll
dev_langs: C++
helpviewer_keywords: UpdateAll method
ms.assetid: e5b26c0a-40fc-4c91-a293-5084951788e6
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 048db34bd08ab3db5769fbcb096578a7a6ae8073
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetupdateall"></a>CRowset::UpdateAll
传输任何挂起的更改对所有行进行自上次提取或**更新**对其调用。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT UpdateAll(   
   DBCOUNTITEM* pcRows = NULL,   
   HROW** pphRow = NULL,   
   DBROWSTATUS** ppStatus = NULL    
) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `pcRows`  
 [out]指向的位置其中`UpdateAll`返回它试图更新，如果所需的行数。  
  
 `pphRow`  
 [out]指向在其中的内存的指针`UpdateAll`返回它尝试更新行的句柄。 如果返回没有句柄`pphRow`为 null。  
  
 `ppStatus`  
 [out]指向的位置其中**更新**返回的行状态值。 如果返回没有状态`ppStatus`为 null。  
  
## <a name="remarks"></a>备注  
 传输任何挂起的更改，因为这些行上次提取或更新使用对所有行进行[更新](../../data/oledb/crowset-update.md)或`UpdateAll`。 `UpdateAll`将更新已被修改，而不考虑是否仍有句柄为它们的每个行 (请参阅`pphRow`) 或不。  
  
 例如，如果你使用**插入**若要在行集中插入五个行，你可以调用**更新**五次或致电`UpdateAll`一次更新所有它们。  
  
 此方法要求的可选接口`IRowsetUpdate`，这可能不支持对所有提供程序，如果出现这种情况，该方法返回**E_NOINTERFACE**。 你还必须设置**DBPROP_IRowsetUpdate**到`VARIANT_TRUE`之前调用**打开**对表或命令，其中包含行集。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [Crowset:: Setdata](../../data/oledb/crowset-setdata.md)   
 [CRowset::Update](../../data/oledb/crowset-update.md)