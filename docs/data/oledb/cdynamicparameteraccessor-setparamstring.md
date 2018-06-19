---
title: 'Cdynamicparameteraccessor:: Setparamstring |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicParameterAccessor.SetParamString
- ATL::CDynamicParameterAccessor::SetParamString
- SetParamString
- CDynamicParameterAccessor::SetParamString
- CDynamicParameterAccessor.SetParamString
dev_langs:
- C++
helpviewer_keywords:
- SetParamString method
ms.assetid: 77a38d23-7e33-4e5a-bda6-c12c4c3fe2e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0b8c435fea707317c1f8de798796f49cb8b048ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095724"
---
# <a name="cdynamicparameteraccessorsetparamstring"></a>CDynamicParameterAccessor::SetParamString
设置存储在缓冲区中的指定参数的字符串数据。  
  
## <a name="syntax"></a>语法  
  
```
bool SetParamString(DBORDINAL nParam,   
   constCHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK) throw();bool SetParamString(DBORDINAL nParam,   
   constWCHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `nParam`  
 [in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关示例。  
  
 `pString`  
 [in]指向 ANSI (**CHAR**) 或 Unicode (**WCHAR**) 的字符串的指定参数的数据。 请参阅`DBSTATUS`oledb.h 中。  
  
 *status*  
 [in]`DBSTATUS`的指定参数的状态。 有关信息`DBSTATUS`值，请参阅[状态](https://msdn.microsoft.com/en-us/library/ms722617.aspx)中*OLE DB 程序员参考*，或搜索`DBSTATUS`oledb.h 中。  
  
## <a name="remarks"></a>备注  
 返回**true**成功或**false**失败。  
  
 `SetParamString` 如果你尝试设置大于为指定的最大大小的字符串将失败`pString`。  
  
 使用`SetParamString`将字符串参数数据设置缓冲区中。 使用[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)将非字符串参数数据设置缓冲区中。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)