---
title: 'Crowset:: Getoriginaldata |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CRowset<TAccessor>.GetOriginalData
- CRowset<TAccessor>::GetOriginalData
- GetOriginalData
- ATL::CRowset<TAccessor>::GetOriginalData
- ATL.CRowset.GetOriginalData
- CRowset::GetOriginalData
- ATL::CRowset::GetOriginalData
- CRowset.GetOriginalData
dev_langs:
- C++
helpviewer_keywords:
- GetOriginalData method
ms.assetid: 5b69d30e-34f4-41a4-a82d-cd175be88d53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 65c0966d60b2498117ac30dc137307a274911e54
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098402"
---
# <a name="crowsetgetoriginaldata"></a>CRowset::GetOriginalData
调用**IRowsetUpdate::GetOriginalData**检索最近从提取或传输到数据源的数据。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetOriginalData() throw();  
  
```  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此方法检索的数据从最近提取或传输到数据源;它不检索基于挂起的更改的值。  
  
 此方法要求的可选接口`IRowsetUpdate`，这可能不支持对所有提供程序，如果出现这种情况，该方法返回**E_NOINTERFACE**。 你还必须设置**DBPROP_IRowsetUpdate**到`VARIANT_TRUE`之前调用**打开**对表或命令，其中包含行集。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::GetOriginalData](https://msdn.microsoft.com/en-us/library/ms709947.aspx)