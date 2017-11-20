---
title: "Icommandimpl:: Getdbsession |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
dev_langs: C++
helpviewer_keywords: GetDBSession method
ms.assetid: e5b1cb13-453f-4698-90bf-f6bfe6814a54
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bb4a4f378d1446e722404a76a19d592a9eed0e20
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="icommandimplgetdbsession"></a>ICommandImpl::GetDBSession
返回到创建该命令的会话中的接口指针。  
  
## <a name="syntax"></a>语法  
  
```  
  
      STDMETHOD (GetDBSession) (  
   REFIID riid,  
   IUnknown** ppSession   
);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[ICommand::GetDBSession](https://msdn.microsoft.com/en-us/library/ms719622.aspx)中*OLE DB 程序员参考*。  
  
## <a name="remarks"></a>备注  
 用于从会话中检索属性。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [ICommandImpl 类](../../data/oledb/icommandimpl-class.md)