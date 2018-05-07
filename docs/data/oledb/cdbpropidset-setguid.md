---
title: 'Cdbpropidset:: Setguid |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- SetGUID
- ATL.CDBPropIDSet.SetGUID
- CDBPropIDSet::SetGUID
dev_langs:
- C++
helpviewer_keywords:
- SetGUID method
ms.assetid: 8dd0f3bf-1490-4d53-9063-322b8d821bbe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 87878b6cc7ae38f2c9ffcf597a56ab020d8e9c8b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdbpropidsetsetguid"></a>CDBPropIDSet::SetGUID
设置中的 GUID 字段**DBPROPIDSET**结构。  
  
## <a name="syntax"></a>语法  
  
```cpp
      void SetGUID(const GUID& guid) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `guid`  
 [in]用于设置 GUID **guidPropertySet**字段[DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx)结构。  
  
## <a name="remarks"></a>备注  
 可以通过设置此字段[构造函数](../../data/oledb/cdbpropidset-cdbpropidset.md)以及。 如果您对此类使用默认构造函数，则调用此函数。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDBPropIDSet 类](../../data/oledb/cdbpropidset-class.md)