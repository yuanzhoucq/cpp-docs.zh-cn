---
title: "ICommandImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandImpl
dev_langs:
- C++
helpviewer_keywords:
- ICommandImpl class
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ec1c9bb3a430b30350ca3940fc7c90e6758d7c40
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="icommandimpl-class"></a>ICommandImpl 类
提供有关实现[ICommand](https://msdn.microsoft.com/en-us/library/ms709737.aspx)接口。  
  
## <a name="syntax"></a>语法

```cpp
template <class T, class CommandBase = ICommand>   
class ATL_NO_VTABLE ICommandImpl : public CommandBase  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`ICommandImpl`。  
  
 `CommandBase`  
 命令界面。 默认值为 `ICommand`。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)|取消当前的命令执行。|  
|[取消](../../data/oledb/icommandimpl-cancel.md)|取消当前的命令执行。|  
|[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)|创建一个行集对象。|  
|[Execute](../../data/oledb/icommandimpl-execute.md)|执行的命令。|  
|[GetDBSession](../../data/oledb/icommandimpl-getdbsession.md)|返回到创建该命令的会话中的接口指针。|  
|[ICommandImpl](../../data/oledb/icommandimpl-icommandimpl.md)|构造函数。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_bCancel](../../data/oledb/icommandimpl-m-bcancel.md)|指示是否要取消命令。|  
|[m_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)|指示是否要取消时执行该命令。|  
|[m_bIsExecuting](../../data/oledb/icommandimpl-m-bisexecuting.md)|指示当前正在执行该命令。|  
  
## <a name="remarks"></a>备注  
 命令对象上的必需接口。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)