---
title: 'Irowsetimpl:: M_breset |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
dev_langs:
- C++
helpviewer_keywords:
- m_bReset
ms.assetid: d423f9f3-4d48-4d0c-b152-684c81a0b34e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9aec38e3cf7e9a58c4fe99d06f35ae55cfdf81c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetimplmbreset"></a>IRowsetImpl::m_bReset
一个位标志，用于确定是否行集上定义的光标位置。  
  
## <a name="syntax"></a>语法  
  
```cpp
unsigned m_bReset:1;  
  
```  
  
## <a name="remarks"></a>备注  
 如果使用者调用[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)与一个负数`lOffset`或*cRows*和`m_bReset`为 true，`GetNextRows`将移到行集结尾。 如果`m_bReset`为 false，使用者接收符合 OLE DB 规范中的错误代码。 `m_bReset`标志获取设置为**true**首先创建行集的是，当使用者调用[irowsetimpl:: Restartposition](../../data/oledb/irowsetimpl-restartposition.md)。 获取设置为**false**当调用`GetNextRows`。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)