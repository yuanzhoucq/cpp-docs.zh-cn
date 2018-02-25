---
title: CRowsetImpl::m_rgRowData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRowsetImpl.m_rgRowData
- CRowsetImpl::m_rgRowData
dev_langs:
- C++
helpviewer_keywords:
- m_rgRowData
ms.assetid: e4e75ca7-12e8-4a0b-94e8-e395c21385b2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ecb6cb3b8bb840cb75a91f0e5674e4bab5c0dc67
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetimplmrgrowdata"></a>CRowsetImpl::m_rgRowData
默认情况下， `CAtlArray` ，对到的用户记录的模板自变量 templatizes `CRowsetImpl`。  
  
## <a name="syntax"></a>语法  
  
```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;  
  
```  
  
## <a name="remarks"></a>备注  
 **ArrayType**是模板参数到`CRowsetImpl`。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [CRowsetImpl 类](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)   
 [CRowsetImpl::m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)