---
title: "Cdatasource:: Getproperty |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
dev_langs:
- C++
helpviewer_keywords:
- GetProperty method
ms.assetid: 6531147c-b164-4ab5-a4a7-509634b85b4d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d12c6bc45c7caac743d996924070dd0c8e5d350c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cdatasourcegetproperty"></a>CDataSource::GetProperty
返回连接的数据源对象的指定属性的值。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetProperty(const GUID& guid,   
   DBPROPID propid,   
   VARIANT* pVariant) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 `guid`  
 [in]一个标识设置为其返回的属性的属性的 GUID。  
  
 `propid`  
 [in]属性 ID 的属性返回。  
  
 *pVariant*  
 [out]指向该变体的其中**GetProperty**返回属性的值。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 若要获取多个属性，请使用[GetProperties](../../data/oledb/cdatasource-getproperties.md)。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDataSource 类](../../data/oledb/cdatasource-class.md)