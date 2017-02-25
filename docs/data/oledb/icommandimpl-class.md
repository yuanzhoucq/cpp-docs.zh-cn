---
title: "ICommandImpl 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICommandImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandImpl 类"
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ICommandImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

针对 [ICommand](https://msdn.microsoft.com/en-us/library/ms709737.aspx) 接口的实现。  
  
## 语法  
  
```  
template <class T, class CommandBase = ICommand>   
class ATL_NO_VTABLE ICommandImpl : public CommandBase  
```  
  
#### 参数  
 `T`  
 类，从 `ICommandImpl`中派生。  
  
 `CommandBase`  
 命令接口。  默认值为 `ICommand`。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)|取消当前的命令执行。|  
|[取消](../../data/oledb/icommandimpl-cancel.md)|取消当前的命令执行。|  
|[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)|创建行集合对象。|  
|[执行](../../data/oledb/icommandimpl-execute.md)|执行命令。|  
|[GetDBSession](../../data/oledb/icommandimpl-getdbsession.md)|返回接口指针。创建命令的会话。|  
|[ICommandImpl](../../data/oledb/icommandimpl-icommandimpl.md)|构造函数。|  
  
### 数据成员  
  
|||  
|-|-|  
|[m\_bCancel](../../data/oledb/icommandimpl-m-bcancel.md)|指示命令是否将取消。|  
|[m\_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)|指示命令是否移除，当完成以后。|  
|[m\_bIsExecuting](../../data/oledb/icommandimpl-m-bisexecuting.md)|指示命令当前是否正在执行。|  
  
## 备注  
 在命令的对象强制接口。  
  
## 要求  
 **页眉：**atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)