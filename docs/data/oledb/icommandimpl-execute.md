---
title: 'Icommandimpl:: Execute |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandImpl::Execute
- ICommandImpl.Execute
dev_langs:
- C++
helpviewer_keywords:
- Execute method
ms.assetid: 033e0d4e-256b-4eed-9215-70e0bebb768c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 369c60c1f6407856fb204654794c214fd9ee8b57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100764"
---
# <a name="icommandimplexecute"></a>ICommandImpl::Execute
执行的命令。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT Execute(IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx)中*OLE DB 程序员参考*。  
  
## <a name="remarks"></a>备注  
 请求的传出接口将获取此函数创建的行集对象的接口。  
  
 **执行**调用[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)。 重写以创建多个行集或提供你自己的条件创建不同的行集的默认实现。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [ICommandImpl 类](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)