---
title: 'Cdynamicparameteraccessor:: Getparamstatus |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicParameterAccessor::GetParamStatus
- CDynamicParameterAccessor.GetParamStatus
- ATL.CDynamicParameterAccessor.GetParamStatus
- ATL::CDynamicParameterAccessor::GetParamStatus
- GetParamStatus
dev_langs:
- C++
helpviewer_keywords:
- GetParamStatus method
ms.assetid: 9300225a-616c-4a7d-82d0-8c2ecd4d8185
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5be2b663dfc1fedf9dffdf1d3acb34e58de23269
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096817"
---
# <a name="cdynamicparameteraccessorgetparamstatus"></a>CDynamicParameterAccessor::GetParamStatus
检索存储在缓冲区中的指定参数的状态。  
  
## <a name="syntax"></a>语法  
  
```
bool GetParamStatus(DBORDINAL nParam,  
  DBSTATUS* pStatus);  

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 `nParam`  
 [in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关示例。  
  
 `pStatus`  
 [out]指向包含的变量的指针`DBSTATUS`的指定参数的状态。 有关信息`DBSTATUS`值，请参阅[状态](https://msdn.microsoft.com/en-us/library/ms722617.aspx)中*OLE DB 程序员参考*，或搜索`DBSTATUS`oledb.h 中。  
  
## <a name="remarks"></a>备注  
 第一重写返回**true**成功或**false**失败。 第二个重写指向包含指定参数的状态的内存。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)