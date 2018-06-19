---
title: 'Crowset:: Getdatahere |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1b77fa67c419ae63547d0e2e90a75333b09984b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091153"
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
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [CRowset::GetData](../../data/oledb/crowset-getdata.md)