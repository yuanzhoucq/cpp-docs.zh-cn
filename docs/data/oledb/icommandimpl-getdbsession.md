---
title: ICommandImpl::GetDBSession | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
dev_langs:
- C++
helpviewer_keywords:
- GetDBSession method
ms.assetid: e5b1cb13-453f-4698-90bf-f6bfe6814a54
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dc7b057d43d0f5b28817fc1b4f4c7c23210ed141
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="icommandimplgetdbsession"></a>ICommandImpl::GetDBSession
返回到创建该命令的会话中的接口指针。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD (GetDBSession) (REFIID riid,  
   IUnknown** ppSession);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[ICommand::GetDBSession](https://msdn.microsoft.com/en-us/library/ms719622.aspx)中*OLE DB 程序员参考*。  
  
## <a name="remarks"></a>备注  
 用于从会话中检索属性。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [ICommandImpl 类](../../data/oledb/icommandimpl-class.md)