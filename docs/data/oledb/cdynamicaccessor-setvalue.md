---
title: CDynamicAccessor::SetValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
dev_langs:
- C++
helpviewer_keywords:
- SetValue method
ms.assetid: ecc18850-96e5-4845-abe5-ab34ad467238
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c919c5ec9605f65df9a20bf5ccad03ae2bf2761c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicaccessorsetvalue"></a>CDynamicAccessor::SetValue
将数据存储到指定的列。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template <class ctype>
bool SetValue(   
   DBORDINAL nColumn,   
   constctype& data) throw( );  

template <class ctype>    
bool SetValue(   
   const CHAR * pColumnName,   
   const ctype& data) throw( );  

template <class ctype>   
bool SetValue(  
   const WCHAR *pColumnName,  
   const ctype& data) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `ctype`  
 [in]处理字符串类型以外的任意数据类型的模板化参数 (**CHAR\***， **WCHAR\***)，这需要特殊处理。 `GetValue` 使用基于此处指定适当的数据类型。  
  
 `pColumnName`  
 [in] 指向包含列名的字符串的指针。  
  
 `data`  
 [in]指向包含数据的内存指针。  
  
 `nColumn`  
 [in] 列号。 列编号从 1 开始。 值为 0 引用的书签列中，如果有的话。  
  
## <a name="return-value"></a>返回值  
 如果你想要设置字符串数据，使用的非模板化版本`GetValue`。 此方法的非模板化版本都会返回**void\***，它指向包含指定的列数据的缓冲区的一部分。 返回**NULL**如果找不到列。  
  
 对于所有其他数据类型，它会更易于使用的模板化版本`GetValue`。 模板化版本都会返回**true**成功或**false**失败。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)