---
title: "ICommandImpl::m_bIsExecuting | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICommandImpl.m_bIsExecuting"
  - "ATL::ICommandImpl::m_bIsExecuting"
  - "m_bIsExecuting"
  - "ATL.ICommandImpl.m_bIsExecuting"
  - "ICommandImpl::m_bIsExecuting"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_bIsExecuting"
ms.assetid: 1e152164-514c-4116-88a3-16984af99991
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ICommandImpl::m_bIsExecuting
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指示命令当前是否不可见。  
  
## 语法  
  
```  
  
unsigned m_bIsExecuting:1;  
  
```  
  
## 备注  
 命令类的 **执行** 方法可以设置此变量为 **true**。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [ICommandImpl 类](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::m\_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)