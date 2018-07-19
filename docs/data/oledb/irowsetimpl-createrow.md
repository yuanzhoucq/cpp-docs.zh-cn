---
title: 'Irowsetimpl:: Createrow |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
dev_langs:
- C++
helpviewer_keywords:
- CreateRow method
ms.assetid: b01c430c-9484-4fef-a6cf-a2e8d9d99130
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eae3fbdce1db5760d4ee5ca75e007c01e98b7bed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103237"
---
# <a name="irowsetimplcreaterow"></a>IRowsetImpl::CreateRow
由调用一个帮助器方法[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)分配一个新**HROW**。  
  
## <a name="syntax"></a>语法  
  
```
HRESULT CreateRow(DBROWOFFSET lRowsOffset,  
  DBCOUNTITEM& cRowsObtained,  
   HROW* rgRows);  
```  
  
#### <a name="parameters"></a>参数  
 *lRowsOffset*  
 正在创建的行的光标位置。  
  
 *cRowsObtained*  
 引用传递回用户，该值指示创建的行数。  
  
 *rgRows*  
 数组**HROW**s 返回新创建的行句柄调用方。  
  
## <a name="remarks"></a>备注  
 如果行存在，此方法调用[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)并返回。 否则为它分配 RowClass 模板变量的新实例并将其添加到[m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)