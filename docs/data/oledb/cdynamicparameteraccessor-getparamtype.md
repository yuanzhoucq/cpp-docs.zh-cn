---
title: CDynamicParameterAccessor::GetParamType | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicParameterAccessor.GetParamType
- CDynamicParameterAccessor:GetParamType
- CDynamicParameterAccessor::GetParamType
- ATL.CDynamicParameterAccessor.GetParamType
- GetParamType
- ATL::CDynamicParameterAccessor::GetParamType
dev_langs:
- C++
helpviewer_keywords:
- GetParamType method
ms.assetid: d9c46775-c2a6-4100-8b69-99f13c52958b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0c5c531cb053397c2629c3232e41b8976fe947c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097775"
---
# <a name="cdynamicparameteraccessorgetparamtype"></a>CDynamicParameterAccessor::GetParamType
检索指定参数的数据类型。  
  
## <a name="syntax"></a>语法  
  
```
bool GetParamType(DBORDINAL nParam,  
  DBTYPE* pType) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 `nParam`  
 [in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关示例。  
  
 `pType`  
 [out]指向包含指定的参数的数据类型的变量的指针。  
  
## <a name="return-value"></a>返回值  
 返回**true**成功或**false**失败。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)