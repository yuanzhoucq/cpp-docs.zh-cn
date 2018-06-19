---
title: 'Irowsetupdateimpl:: M_mapcacheddata |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
dev_langs:
- C++
helpviewer_keywords:
- m_mapCachedData
ms.assetid: 65131743-8580-48c8-bb22-68f17c9dfa13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bd19f8706e50d1eefb26dadfb837d8bd4f13f061
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103250"
---
# <a name="irowsetupdateimplmmapcacheddata"></a>IRowsetUpdateImpl::m_mapCachedData
包含该延迟操作的原始数据的映射。  
  
## <a name="syntax"></a>语法  
  
```cpp
      CAtlMap<   
   HROW hRow,    
   Storage* pData   
>   
m_mapCachedData;  
```  
  
#### <a name="parameters"></a>参数  
 `hRow`  
 数据行的句柄。  
  
 `pData`  
 指向要缓存的数据的指针。 类型的数据为*存储*（用户记录类）。 请参阅*存储*中的模板自变量[IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)