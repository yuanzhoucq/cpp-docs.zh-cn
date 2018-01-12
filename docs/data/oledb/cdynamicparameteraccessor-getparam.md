---
title: "Cdynamicparameteraccessor:: Getparam |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicParameterAccessor::GetParam
- ATL.CDynamicParameterAccessor.GetParam
- CDynamicParameterAccessor::GetParam<ctype>
- CDynamicParameterAccessor.GetParam
- GetParam
- ATL::CDynamicParameterAccessor::GetParam<ctype>
- ATL::CDynamicParameterAccessor::GetParam
dev_langs: C++
helpviewer_keywords: GetParam method
ms.assetid: 893a6bf8-7b55-4f6d-8a10-a43b13be7f56
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7cdd27cfdd173e556bb9d4c6fd27a9d801a7f8c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicparameteraccessorgetparam"></a>CDynamicParameterAccessor::GetParam
从参数缓冲区中检索指定参数的非字符串数据。  
  
## <a name="syntax"></a>语法  
  
```  
  
      template < class ctype > bool GetParam(   
   DBORDINAL nParam,   
   ctype* pData    
) const throw( );  
template < class ctype > bool GetParam(   
   TCHAR* pParamName,   
   ctype* pData    
) const throw( );  
void* GetParam(   
   DBORDINAL nParam    
) const throw( );  
void* GetParam(   
   TCHAR* pParamName    
) const throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `ctype`  
 数据类型是一个模板化参数。  
  
 `nParam`  
 [in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关示例。  
  
 `pParamName`  
 [in]参数名称。  
  
 `pData`  
 [out]指向包含从缓冲区检索的数据的内存指针。  
  
## <a name="return-value"></a>返回值  
 对于非模板化版本，指向包含数据的内存从缓冲区中检索。 对于模板化版本，返回**true**成功或**false**失败。  
  
 使用`GetParam`从缓冲区中检索非字符串参数数据。 使用[GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md)从缓冲区中检索字符串参数数据。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)