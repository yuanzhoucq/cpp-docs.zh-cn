---
title: "Crowsetimpl:: Setcommandtext |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
dev_langs: C++
helpviewer_keywords: SetCommandText method
ms.assetid: e016d7df-c1a0-4dee-b19b-c876680221fd
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a33af61311b9c202e5e0c68579ac4f21afd98f94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetimplsetcommandtext"></a>CRowsetImpl::SetCommandText
验证并将存储**DBID**两个字符串中的 s ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md))。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT CRowsetBaseImpl::SetCommandText(  
   DBID* pTableID,  
   DBID* pIndexID   
);  
```  
  
#### <a name="parameters"></a>参数  
 `pTableID`  
 [in]指向的指针**DBID**表示表 id。  
  
 `pIndexID`  
 [in]指向的指针**DBID**表示索引 id。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 **SetCommentText**方法由调用`CreateRowset`，静态模板化的方法`IOpenRowsetImpl`。  
  
 此方法将其工作委托通过调用[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)和[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)通过一个向上转换的指针。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [CRowsetImpl 类](../../data/oledb/crowsetimpl-class.md)