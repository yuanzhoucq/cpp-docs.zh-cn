---
title: "Ierrorrecordsimpl:: Geterrorhelpfile |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IErrorRecordsImpl::GetErrorHelpFile
- GetErrorHelpFile
- IErrorRecordsImpl.GetErrorHelpFile
dev_langs: C++
helpviewer_keywords: GetErrorHelpFile method
ms.assetid: ad198f76-5bdf-4b8d-9f1a-3d38f72f31ad
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a244cffcb7e2b6e6b1ff5c266ee846ba33b13e8e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ierrorrecordsimplgeterrorhelpfile"></a>IErrorRecordsImpl::GetErrorHelpFile
从错误记录中获取的帮助文件的路径名称。  
  
## <a name="syntax"></a>语法  
  
```  
  
      LPOLESTR GetErrorHelpFile(  
   ERRORINFO& rCurError   
);  
```  
  
#### <a name="parameters"></a>参数  
 `rCurError`  
 `ERRORINFO`中记录**IErrorInfo**接口。  
  
## <a name="return-value"></a>返回值  
 指向包含错误的帮助文件的路径名称的字符串的指针。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IErrorRecordsImpl 类](../../data/oledb/ierrorrecordsimpl-class.md)