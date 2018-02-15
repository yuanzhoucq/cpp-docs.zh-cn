---
title: CDynamicParameterAccessor::SetParam | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor.SetParam
- ATL.CDynamicParameterAccessor.SetParam
- SetParam
- CDynamicParameterAccessor:SetParam
- CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor::SetParam
dev_langs:
- C++
helpviewer_keywords:
- SetParam method
ms.assetid: e2349220-545c-46ad-90da-9113ac52551a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1c6868c9ced5524dcd218d61206c3993ccadd7f8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicparameteraccessorsetparam"></a>CDynamicParameterAccessor::SetParam
设置使用指定的 （非字符串） 数据的参数缓冲区。  
  
## <a name="syntax"></a>语法  
  
```cpp
template <class ctype>
bool SetParam(DBORDINAL nParam,  
               constctype* pData,  
               DBSTATUS status = DBSTATUS_S_OK) throw();  

template <class ctype>  
bool SetParam(TCHAR* pParamName,  
               const ctype* pData,  
               DBSTATUS status = DBSTATUS_S_OK) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `ctype`  
 数据类型是一个模板化参数。  
  
 `nParam`  
 [in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 例如:  
  
 [!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]  
  
 `pParamName`  
 [in]参数名称。  
  
 `pData`  
 [in]指向包含要写入缓冲区的数据的内存指针。  
  
 *status*  
 [in]`DBSTATUS`列状态。 有关信息`DBSTATUS`值，请参阅[状态](https://msdn.microsoft.com/en-us/library/ms722617.aspx)中*OLE DB 程序员参考*，或搜索`DBSTATUS`oledb.h 中。  
  
## <a name="return-value"></a>返回值  
 返回**true**成功或**false**失败。  
  
 使用`SetParam`将非字符串参数数据设置缓冲区中。 使用[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)将字符串参数数据设置缓冲区中。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)