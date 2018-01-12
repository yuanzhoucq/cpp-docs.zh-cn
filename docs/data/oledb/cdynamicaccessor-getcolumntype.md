---
title: "Cdynamicaccessor:: Getcolumntype |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDynamicAccessor.GetColumnType
- CDynamicAccessor::GetColumnType
- GetColumnType
- CDynamicAccessor.GetColumnType
- ATL::CDynamicAccessor::GetColumnType
dev_langs: C++
helpviewer_keywords: GetColumnType method
ms.assetid: ac96a2e9-6049-4eb5-9718-9f5f5446b74e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dedacd68de5a254d138326a4030511685ab0da2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicaccessorgetcolumntype"></a>CDynamicAccessor::GetColumnType
检索指定列的数据类型。  
  
## <a name="syntax"></a>语法  
  
```  
  
      bool GetColumnType(   
   DBORDINAL nColumn,   
   DBTYPE* pType    
) const throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `nColumn`  
 [in] 列号。 列编号从 1 开始。 值为 0 引用的书签列中，如果有的话。  
  
 `pType`  
 [out]指向指定列的数据类型的指针。  
  
## <a name="return-value"></a>返回值  
 返回**true**成功或**false**失败。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx)