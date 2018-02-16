---
title: IRowsetImpl::m_bReset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1ca38b0fa56f901d18e90d3305c92cc097452369
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetimplmbreset"></a>IRowsetImpl::m_bReset
一个位标志，用于确定是否行集上定义的光标位置。  
  
## <a name="syntax"></a>语法  
  
```cpp
unsigned m_bReset:1;  
  
```  
  
## <a name="remarks"></a>备注  
 如果使用者调用[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)与一个负数`lOffset`或*cRows*和`m_bReset`为 true，`GetNextRows`将移到行集结尾。 如果`m_bReset`为 false，使用者接收符合 OLE DB 规范中的错误代码。 `m_bReset`标志获取设置为**true**首先创建行集的是，当使用者调用[irowsetimpl:: Restartposition](../../data/oledb/irowsetimpl-restartposition.md)。 获取设置为**false**当调用`GetNextRows`。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)