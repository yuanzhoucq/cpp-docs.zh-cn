---
title: "Ierrorrecordsimpl:: Geterrorguid |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetErrorGUID
- IErrorRecordsImpl.GetErrorGUID
- IErrorRecordsImpl::GetErrorGUID
dev_langs: C++
helpviewer_keywords: GetErrorGUID method
ms.assetid: 42c00755-50e5-401a-8246-adef9de5ced2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a2b1ec6a783bc5b289a024be2b64917b064e581e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ierrorrecordsimplgeterrorguid"></a>IErrorRecordsImpl::GetErrorGUID
获取从错误记录错误 GUID。  
  
## <a name="syntax"></a>语法  
  
```  
  
      REFGUID GetErrorGUID(  
   ERRORINFO& rCurError   
);  
```  
  
#### <a name="parameters"></a>参数  
 `rCurError`  
 `ERRORINFO`中记录**IErrorInfo**接口。  
  
## <a name="return-value"></a>返回值  
 对错误的 GUID 的引用。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [IErrorRecordsImpl 类](../../data/oledb/ierrorrecordsimpl-class.md)