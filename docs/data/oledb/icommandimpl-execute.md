---
title: "ICommandImpl::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICommandImpl::Execute"
  - "ICommandImpl.Execute"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Execute 方法"
ms.assetid: 033e0d4e-256b-4eed-9215-70e0bebb768c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ICommandImpl::Execute
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

执行命令。  
  
## 语法  
  
```  
  
      HRESULT Execute(  
   IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset   
);  
```  
  
#### 参数  
 参见[ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) ，在 *OLE DB Programmer's Reference.*中。  
  
## 备注  
 请求的传出接口是从行集合获取此函数创建的对象的接口。  
  
 **执行** 调用 [CreateRowset](../../data/oledb/icommandimpl-createrowset.md)。  重写默认的实现创建多行集或提供您自己创建的不同的行条件。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [ICommandImpl 类](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)