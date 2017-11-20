---
title: "Cdynamicparameteraccessor:: Setparamstatus |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicParameterAccessor::SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamStatus
- ATL::CDynamicParameterAccessor::SetParamStatus
- CDynamicParameterAccessor.SetParamStatus
- SetParamStatus
dev_langs: C++
helpviewer_keywords: SetParamStatus method
ms.assetid: 0c2271f6-457d-46ca-88b7-4590aadb20d7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8b239000efa761ee30aa44fb8285fa96992e0b0b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicparameteraccessorsetparamstatus"></a>CDynamicParameterAccessor::SetParamStatus
设置存储在缓冲区中的指定参数的状态。  
  
## <a name="syntax"></a>语法  
  
```  
  
      bool SetParamStatus(  
   DBORDINAL nParam,  
   DBSTATUS status  
);  
```  
  
#### <a name="parameters"></a>参数  
 `nParam`  
 [in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关示例。  
  
 *status*  
 [in]`DBSTATUS`的指定参数的状态。 有关信息`DBSTATUS`值，请参阅[状态](https://msdn.microsoft.com/en-us/library/ms722617.aspx)中*OLE DB 程序员参考*，或搜索`DBSTATUS`oledb.h 中。  
  
## <a name="remarks"></a>备注  
 返回**true**成功或**false**失败。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>另请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)