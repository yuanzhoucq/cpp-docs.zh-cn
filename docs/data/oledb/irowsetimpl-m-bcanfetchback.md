---
title: 'Irowsetimpl:: M_bcanfetchback |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
dev_langs:
- C++
helpviewer_keywords:
- m_bCanFetchBack
ms.assetid: cfa007b0-7ba5-48a3-9d05-9f1916305fb7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bf194fc7d7547cf03194f4dd5bedf014c9101b0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetimplmbcanfetchback"></a>IRowsetImpl::m_bCanFetchBack
指示提供程序是否支持向后提取。  
  
## <a name="syntax"></a>语法  
  
```cpp
unsigned m_bCanFetchBack:1;  
  
```  
  
## <a name="remarks"></a>备注  
 链接至**DBPROP_CANFETCHBACKWARDS**中的属性**DBPROPSET_ROWSET**组。 提供程序必须支持**DBPROP_CANFETCHBACKWARDS**为**m_bCanFetchBackwards**为 true。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::m_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)