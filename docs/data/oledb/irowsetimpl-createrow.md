---
title: "IRowsetImpl::CreateRow | Microsoft Docs"
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
  - "IRowsetImpl.CreateRow"
  - "ATL.IRowsetImpl.CreateRow"
  - "ATL::IRowsetImpl::CreateRow"
  - "CreateRow"
  - "IRowsetImpl::CreateRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateRow 方法"
ms.assetid: b01c430c-9484-4fef-a6cf-a2e8d9d99130
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::CreateRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) 调用的帮助器方法将新的 **HROW**。  
  
## 语法  
  
```  
  
      HRESULT CreateRow(  
   DBROWOFFSET lRowsOffset,  
   DBCOUNTITEM& cRowsObtained,  
   HROW* rgRows   
);  
```  
  
#### 参数  
 *lRowsOffset*  
 创建行的光标位置。  
  
 *cRowsObtained*  
 引用传递给回指示要创建的用户。  
  
 *rgRows*  
 **HROW**数组中返回到包含新生成的行句柄的调用方。  
  
## 备注  
 如果行存在，此方法调用将返回。[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) 否则，它将 RowClass 模板变量的新实例并将其添加到。[m\_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)