---
title: 'Crowsetimpl:: Validatecommandid |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
dev_langs:
- C++
helpviewer_keywords:
- ValidateCommandID method
ms.assetid: cdde6088-41bc-4b8f-a32b-f36f7d9b5ec0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6b83f0e8bb65a6043a9ca48f87ffe8babfb73e22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098493"
---
# <a name="crowsetimplvalidatecommandid"></a>CRowsetImpl::ValidateCommandID
检查和 / 或如果，请参阅**DBID**s 包含字符串值，并且如果是这样，则将它们复制到其数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>参数  
 `pTableID`  
 [in]指向的指针**DBID**表示表 id。  
  
 `pIndexID`  
 [in]指向的指针**DBID**表示索引 id。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 通过静态将向上转换通过调用此方法`CRowsetImpl`来填充其数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。 默认情况下，此方法检查和 / 或如果，请参阅**DBID**s 包含字符串值，并且如果是这样，则将它们复制到其数据成员。 通过将具有此签名中的方法你`CRowsetImpl`-派生类，而不是基实现，将调用您的方法。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [CRowsetImpl 类](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)