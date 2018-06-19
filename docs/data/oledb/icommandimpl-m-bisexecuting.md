---
title: 'Icommandimpl:: M_bisexecuting |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandImpl.m_bIsExecuting
- ATL::ICommandImpl::m_bIsExecuting
- m_bIsExecuting
- ATL.ICommandImpl.m_bIsExecuting
- ICommandImpl::m_bIsExecuting
dev_langs:
- C++
helpviewer_keywords:
- m_bIsExecuting
ms.assetid: 1e152164-514c-4116-88a3-16984af99991
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d4e445ccee027aa980c2c651d04d9473321a6b56
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099896"
---
# <a name="icommandimplmbisexecuting"></a>ICommandImpl::m_bIsExecuting
指示当前正在执行该命令。  
  
## <a name="syntax"></a>语法  
  
```cpp
unsigned m_bIsExecuting:1;  
  
```  
  
## <a name="remarks"></a>备注  
 **执行**命令类的方法可以将此变量设置为**true**。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [ICommandImpl 类](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::m_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)