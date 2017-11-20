---
title: "Ierrorrecordsimpl:: Adderrorrecord |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IErrorRecordsImpl.AddErrorRecord
- AddErrorRecord
- IErrorRecordsImpl::AddErrorRecord
dev_langs: C++
helpviewer_keywords: AddErrorRecord method
ms.assetid: b5f8e9ae-509d-454f-b511-4bda7e972607
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2962800465c06a0a2c780f26a8e00741db378358
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ierrorrecordsimpladderrorrecord"></a>IErrorRecordsImpl::AddErrorRecord
将记录添加到 OLE DB 错误对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
      STDMETHOD( AddErrorRecord )(  
   ERRORINFO *pErrorInfo,  
   DWORD dwLookupID,  
   DISPPARAMS *pdispparams,  
   IUnknown *punkCustomError,  
   DWORD dwDynamicErrorID   
);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IErrorRecords::AddErrorRecord](https://msdn.microsoft.com/en-us/library/ms725362.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [IErrorRecordsImpl 类](../../data/oledb/ierrorrecordsimpl-class.md)