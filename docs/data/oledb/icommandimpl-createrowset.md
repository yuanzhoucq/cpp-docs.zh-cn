---
title: "ICommandImpl::CreateRowset | Microsoft Docs"
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
  - "ICommandImpl::CreateRowset"
  - "ICommandImpl.CreateRowset"
  - "CreateRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateRowset 方法"
ms.assetid: a0890009-205e-4970-879f-01ed9d6a93f1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandImpl::CreateRowset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用 [执行](../../data/oledb/icommandimpl-execute.md) 创建单个行集合。  
  
## 语法  
  
```  
  
      template <class   
      RowsetClass  
      >  
HRESULT CreateRowset(  
   IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj   
);  
```  
  
#### 参数  
 `RowsetClass`  
 表示用户的行集合类的模板类的成员。  通常会通过向导产生。  
  
 `pUnkOuter`  
 \[in\] 给控制 **IUnknown** 接口的指针作为聚合的一部分，行集，则创建；否则，该列为空。  
  
 `riid`  
 \[in\] 对应于 `ICommand::Execute`的 `riid`。  
  
 `pParams`  
 \[in\/out\] 对应于 `ICommand::Execute`的 `pParams`。  
  
 `pcRowsAffected`  
 对应于 `pcRowsAffected`，在 `ICommand::Execute`中。  
  
 `ppRowset`  
 \[in\/out\] 对应于 `ICommand::Execute`的 `ppRowset`。  
  
 `pRowsetObj`  
 \[out\] 指向行集合对象的指针。  通常不使用此参数，但是如果在传递到COM 对象之前必须对行集合进行更多的工作，它可以被使用。   `pRowsetObj` 的生存期由 `ppRowset`绑定。  
  
## 返回值  
 标准 `HRESULT` 值。  有关典型值的列表，请参加`ICommand::Execute`。  
  
## 备注  
 创建多行集，或提供您自己创建的不同的行条件，不同的位置调用 `CreateRowset`。**执行**的内部。  
  
 参加 [ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) ，在 *OLE DB Programmer's Reference.*中。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [ICommandImpl 类](../../data/oledb/icommandimpl-class.md)