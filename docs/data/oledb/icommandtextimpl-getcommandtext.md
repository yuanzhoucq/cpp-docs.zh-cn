---
title: 'Icommandtextimpl:: Getcommandtext |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
dev_langs:
- C++
helpviewer_keywords:
- GetCommandText method
ms.assetid: 0f8da470-b1c3-4573-974f-1acc111e3984
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e2f52f17258e4a317f58e40a60583998673f2efd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101079"
---
# <a name="icommandtextimplgetcommandtext"></a>ICommandTextImpl::GetCommandText
返回的文本命令集的最后一个调用[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(GetCommandText)(GUID * pguidDialect,   
   LPOLESTR * ppwszCommand);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx)中*OLE DB 程序员参考*。 *PguidDialect*默认情况下忽略参数。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [ICommandTextImpl 类](../../data/oledb/icommandtextimpl-class.md)