---
title: CRowset::GetDataHere | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRowset<TAccessor>::GetDataHere
- CRowset<TAccessor>.GetDataHere
- CRowset.GetDataHere
- GetDataHere
- CRowset::GetDataHere
- ATL::CRowset::GetDataHere
- ATL::CRowset<TAccessor>::GetDataHere
- ATL.CRowset<TAccessor>.GetDataHere
- ATL.CRowset.GetDataHere
dev_langs:
- C++
helpviewer_keywords:
- GetDataHere method
ms.assetid: 2fe2a987-1c4c-4299-876e-0591caf63af4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bcd5a70702a2b38fcdc97b431bfdd29a01c60ddf
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetgetdatahere"></a>CRowset::GetDataHere
从当前行中检索数据并将其放到指定的缓冲区。  
  
## <a name="syntax"></a>语法  
  
```
HRESULT GetDataHere(int nAccessor,   
  void* pBuffer) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `nAccessor`  
 [in]访问器可用于访问的数据索引号。  
  
 `pBuffer`  
 [out]到来放置当前记录的数据缓冲区。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 有关如何使用此函数的示例，请参阅[MultiRead 的示例](../../visual-cpp-samples.md)。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [CRowset::GetData](../../data/oledb/crowset-getdata.md)