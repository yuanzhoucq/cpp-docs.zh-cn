---
title: "Irowsetimpl:: Createrow |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
dev_langs: C++
helpviewer_keywords: CreateRow method
ms.assetid: b01c430c-9484-4fef-a6cf-a2e8d9d99130
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2f455935a1736eae2c70d95f4528d216a80e782a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetimplcreaterow"></a>IRowsetImpl::CreateRow
由调用一个帮助器方法[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)分配一个新**HROW**。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT CreateRow(  
   DBROWOFFSET lRowsOffset,  
   DBCOUNTITEM& cRowsObtained,  
   HROW* rgRows   
);  
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
  
## <a name="see-also"></a>另请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)