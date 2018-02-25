---
title: CRowset::GetApproximatePosition | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CRowset::GetApproximatePosition
- ATL::CRowset<TAccessor>::GetApproximatePosition
- CRowset.GetApproximatePosition
- CRowset::GetApproximatePosition
- GetApproximatePosition
- ATL.CRowset.GetApproximatePosition
- CRowset<TAccessor>::GetApproximatePosition
dev_langs:
- C++
helpviewer_keywords:
- GetApproximatePosition method
ms.assetid: 8f9ccd41-0590-468e-b202-6731d0f99d21
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ae92a7734c3b6f763ab4d6731e1cb8ff5222c676
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetgetapproximateposition"></a>CRowset::GetApproximatePosition
返回对应于书签的行的近似位置。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetApproximatePosition(const CBookmarkBase* pBookmark,   
   DBCOUNTITEM* pPosition,   
   DBCOUNTITEM* pcRows) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `pBookmark`  
 [in]指向一个书签，用于标识其位置是要查找的行的指针。 **NULL**如果只是必需的行计数。  
  
 *pPosition*  
 [out]指向的位置其中`GetApproximatePosition`返回的行位置。 **NULL**如果位置不需要。  
  
 `pcRows`  
 [out]指向的位置其中`GetApproximatePosition`返回的行总数。 **NULL**如果行计数不需要。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此方法要求的可选接口`IRowsetScroll`，这可能不支持对所有提供程序，如果出现这种情况，该方法返回**E_NOINTERFACE**。 你还必须设置**DBPROP_IRowsetScroll**到`VARIANT_TRUE`之前调用**打开**对表或命令，其中包含行集。  
  
 在使用者中使用书签的信息，请参阅[使用书签](../../data/oledb/using-bookmarks.md)。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [IRowsetScroll::GetApproximatePosition](https://msdn.microsoft.com/en-us/library/ms712901.aspx)