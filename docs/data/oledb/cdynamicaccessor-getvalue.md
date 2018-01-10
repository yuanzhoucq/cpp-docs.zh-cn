---
title: "Cdynamicaccessor:: Getvalue |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
dev_langs: C++
helpviewer_keywords: GetValue method
ms.assetid: 553f44af-68bc-4cb6-8774-e0940003fa90
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1599cd82347c4074863f2b649a2c67df894893e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicaccessorgetvalue"></a>CDynamicAccessor::GetValue
检索指定列的数据。  
  
## <a name="syntax"></a>语法  
  
```  
  
      void* GetValue(   
   DBORDINAL nColumn    
) const throw( );  
void* GetValue(  
   const CHAR* pColumnName   
) const throw( );  
void* GetValue(  
   const WCHAR* pColumnName   
) const throw( );  
template < class ctype >  
bool GetValue(  
   DBORDINAL nColumn,  
   ctype* pData   
) const throw( );  
template < class ctype >  
bool GetValue(  
   const CHAR* pColumnName,  
   ctype* pData   
) const throw( );  
template < class ctype >  
bool GetValue(  
   const WCHAR* pColumnName,  
   ctype* pData   
) const throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `ctype`  
 [in]处理字符串类型以外的任意数据类型的模板化参数 (**CHAR\***， **WCHAR\***)，这需要特殊处理。 `GetValue`使用基于此处指定适当的数据类型。  
  
 `nColumn`  
 [in] 列号。 列编号从 1 开始。 值为 0 引用的书签列中，如果有的话。  
  
 `pColumnName`  
 [in]列名称。  
  
 `pData`  
 [out]指向指定列的内容的指针。  
  
## <a name="return-value"></a>返回值  
 如果你想要将字符串数据传递，使用的非模板化版本`GetValue`。 此方法的非模板化版本都会返回**void\***，它指向包含指定的列数据的缓冲区的一部分。 返回**NULL**如果找不到列。  
  
 对于所有其他数据类型，它会更易于使用的模板化版本`GetValue`。 模板化版本都会返回**true**成功或**false**失败。  
  
## <a name="remarks"></a>备注  
 使用非模板化版本返回包含字符串和包含其他数据类型的列的模板化版本的列。  
  
 在调试模式下，你将获取断言，如果的大小`pData`是到它所指向列的大小不相等。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)