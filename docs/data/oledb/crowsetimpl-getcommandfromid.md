---
title: "Crowsetimpl:: Getcommandfromid |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowsetImpl::GetCommandFromID
- GetCommandFromID
- CRowsetImpl.GetCommandFromID
dev_langs: C++
helpviewer_keywords: GetCommandFromID method
ms.assetid: 9f39cb07-1c40-486f-ba5b-cb4a65fab8a7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e75fbd00b6ee2e4a19cf0fe39d0bcda9f0314f8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetimplgetcommandfromid"></a>CRowsetImpl::GetCommandFromID
检查以确定如果其中一种或两个参数包含字符串值，并且如果是这样，将字符串值复制到数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT CRowsetBaseImpl::GetCommandFromID(  
   DBID* pTableID,  
   DBID* pIndexID   
);  
```  
  
#### <a name="parameters"></a>参数  
 `pTableID`  
 [in]指向的指针**DBID**表示表的 id。  
  
 `pIndexID`  
 [in]指向的指针**DBID**表示索引 id。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 通过静态将向上转换通过调用此方法`CRowsetImpl`来填充数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。 默认情况下，此方法检查以查看其中一种或两个参数是否包含字符串值。 如果它们包含字符串值，此方法会将字符串值复制到数据成员。 通过将具有此签名中的方法你`CRowsetImpl`-派生类，而不是基实现，将调用您的方法。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [CRowsetImpl 类](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)