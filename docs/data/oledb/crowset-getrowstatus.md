---
title: "Crowset:: Getrowstatus |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords: GetRowStatus method
ms.assetid: 7a29a235-cb7e-40c1-92ce-5441751febee
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: af94964b3aa68348ad976353845d4647f20d1ef9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetgetrowstatus"></a>CRowset::GetRowStatus
返回所有行的状态。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT GetRowStatus(   
   DBPENDINGSTATUS* pStatus    
) const throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `pStatus`  
 [out]指向一个位置的指针其中`GetRowStatus`返回的状态值。 请参阅 OLE DB 程序员参考中的 DBPENDINGSTATUS。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此方法要求的可选接口`IRowsetUpdate`，这可能不支持对所有提供程序，如果出现这种情况，该方法返回**E_NOINTERFACE**。 你还必须设置**DBPROP_IRowsetUpdate**到`VARIANT_TRUE`之前调用**打开**对表或命令，其中包含行集。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/en-us/library/ms724377.aspx)