---
title: "Icommandtextimpl:: Getcommandtext |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
dev_langs: C++
helpviewer_keywords: GetCommandText method
ms.assetid: 0f8da470-b1c3-4573-974f-1acc111e3984
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: df72d8d6e5c3c5c85d1216bf321216aef515a1d8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="icommandtextimplgetcommandtext"></a>ICommandTextImpl::GetCommandText
返回的文本命令集的最后一个调用[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)。  
  
## <a name="syntax"></a>语法  
  
```  
  
      STDMETHOD(GetCommandText)(   
   GUID * pguidDialect,   
   LPOLESTR * ppwszCommand    
);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx)中*OLE DB 程序员参考*。 *PguidDialect*默认情况下忽略参数。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [ICommandTextImpl 类](../../data/oledb/icommandtextimpl-class.md)