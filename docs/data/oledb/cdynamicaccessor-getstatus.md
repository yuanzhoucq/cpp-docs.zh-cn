---
title: 'Cdynamicaccessor:: Getstatus |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDynamicAccessor::GetStatus
- CDynamicAccessor.GetStatus
- ATL.CDynamicAccessor.GetStatus
- CDynamicAccessor::GetStatus
dev_langs:
- C++
helpviewer_keywords:
- GetStatus method
ms.assetid: 8f1aba69-5c2c-4ca7-ad84-7b4b27995eb8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 98e120e19c6115b98ed57bc8d25a934b84573386
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessorgetstatus"></a>CDynamicAccessor::GetStatus
检索指定列的状态。  
  
## <a name="syntax"></a>语法  
  
```
bool GetStatus(DBORDINAL nColumn,   
  DBSTATUS* pStatus) const throw();  

bool GetStatus(const CHAR* pColumnName,  
   DBSTATUS* pStatus) const throw();  

bool GetStatus(const WCHAR* pColumnName,  
   DBSTATUS* pStatus) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 `nColumn`  
 [in] 列号。 列编号从 1 开始。 值为 0 引用的书签列中，如果有的话。  
  
 `pColumnName`  
 [in] 指向包含列名的字符串的指针。  
  
 `pStatus`  
 [out]指向包含的列状态的变量的指针。 请参阅[DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx)中*OLE DB 程序员参考*有关详细信息。  
  
## <a name="return-value"></a>返回值  
 返回**true**如果找到指定的列。 否则，此函数返回**false**。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::SetStatus](../../data/oledb/cdynamicaccessor-setstatus.md)