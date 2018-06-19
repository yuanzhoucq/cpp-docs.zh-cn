---
title: 'Irowsetimpl:: Getdbstatus |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
dev_langs:
- C++
helpviewer_keywords:
- GetDBStatus method
ms.assetid: e51d8ee2-fc0c-4909-861c-026c94fb0dfc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ebebbc2d1392e4f3c863ce366e8d19cfad3b7162
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106526"
---
# <a name="irowsetimplgetdbstatus"></a>IRowsetImpl::GetDBStatus
返回`DBSTATUS`指定字段的状态标志。  
  
## <a name="syntax"></a>语法  
  
```cpp
      virtual DBSTATUS GetDBStatus(RowClass* currentRow,  
   ATLCOLUMNINFO* columnNames);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `currentRow`  
 当前行。  
  
 [in] `columnNames`  
 正在为其请求状态列。  
  
## <a name="return-value"></a>返回值  
 [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx)标志的列。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)