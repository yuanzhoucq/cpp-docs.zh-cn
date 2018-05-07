---
title: 'Cdynamicparameteraccessor:: Getparamstring |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicParameterAccessor.GetParamString
- GetParamString
- CDynamicParameterAccessor::GetParamString
- ATL.CDynamicParameterAccessor.GetParamString
- ATL::CDynamicParameterAccessor::GetParamString
dev_langs:
- C++
helpviewer_keywords:
- GetParamString method
ms.assetid: 078c2b1c-7072-47c1-a203-f47e75363f91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b8dadcb70dd29f1a70aea288eb0f63b22591561e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicparameteraccessorgetparamstring"></a>CDynamicParameterAccessor::GetParamString
检索存储在缓冲区中的指定参数的字符串数据。  
  
## <a name="syntax"></a>语法  
  
```
bool GetParamString(DBORDINAL nParam,  
  CSimpleStringA& strOutput) throw();bool GetParamString(DBORDINAL nParam,  
  CSimpleStringW& strOutput) throw();bool GetParamString(DBORDINAL nParam,  
  CHAR* pBuffer,  
   size_t* pMaxLen) throw();bool GetParamString(DBORDINAL nParam,  
  WCHAR* pBuffer,  
   size_t* pMaxLen) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `nParam`  
 [in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关示例。  
  
 `strOutput`  
 [out]ANSI (**CSimpleStringA**) 或 Unicode (**CSimpleStringW**) 的字符串的指定参数的数据。 应传递的类型参数`CString`，例如：  
  
 [!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]  
  
 `pBuffer`  
 [out]指向 ANSI (**CHAR**) 或 Unicode (**WCHAR**) 的字符串的指定参数的数据。  
  
 `pMaxLen`  
 [out]指向缓冲区的大小的指针指向的`pBuffer`（以字符为单位，包括终止 NULL）。  
  
## <a name="remarks"></a>备注  
 返回**true**成功或**false**失败。  
  
 如果`pBuffer`为 NULL，此方法将在指向的内存中设置所需的缓冲区大小`pMaxLen`并返回**true**而无需复制数据。  
  
 如果此方法将失败缓冲区`pBuffer`足够大，无法包含的整个字符串。  
  
 使用`GetParamString`从缓冲区中检索字符串参数数据。 使用[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)从缓冲区中检索非字符串参数数据。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)