---
title: "ICommandImpl::GetDBSession | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICommandImpl::GetDBSession"
  - "GetDBSession"
  - "ICommandImpl.GetDBSession"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetDBSession 方法"
ms.assetid: e5b1cb13-453f-4698-90bf-f6bfe6814a54
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandImpl::GetDBSession
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回接口指针。创建命令的会话。  
  
## 语法  
  
```  
  
      STDMETHOD (GetDBSession) (  
   REFIID riid,  
   IUnknown** ppSession   
);  
```  
  
#### 参数  
 参阅《*OLE DB 程序员参考》\) 中的*[ICommand::GetDBSession](https://msdn.microsoft.com/en-us/library/ms719622.aspx)。  
  
## 备注  
 用于检索属性从会话。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [ICommandImpl 类](../../data/oledb/icommandimpl-class.md)