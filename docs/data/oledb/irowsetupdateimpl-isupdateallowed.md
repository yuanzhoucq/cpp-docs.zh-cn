---
title: "IRowsetUpdateImpl::IsUpdateAllowed | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetUpdateImpl::IsUpdateAllowed"
  - "IRowsetUpdateImpl.IsUpdateAllowed"
  - "IsUpdateAllowed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsUpdateAllowed 方法"
ms.assetid: d6daf3b3-a8e0-4275-a67d-897dea01e297
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetUpdateImpl::IsUpdateAllowed
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重写此方法来检查安全性，完整性，等等在更新之前。  
  
## 语法  
  
```  
  
      HRESULT IsUpdateAllowed(  
   DBPENDINGSTATUS /* [in] *//* status */,  
   HROW /* [in] *//* hRowUpdate */,  
   DBROWSTATUS* /* [out] *//* pRowStatus */  
);  
```  
  
#### 参数  
 *status*  
 \[in\] 挂起操作状态该行的。  
  
 *hRowUpdate*  
 \[in\] 用于处理用户要更新的行。  
  
 *pRowStatus*  
 \[out\] 状态返回给用户。  
  
## 备注  
 如果确定应允许更新，则返回 `S_OK`;否则返回 **E\_FAIL**。  如果允许更新，您还需要设置。[IRowsetUpdateImpl::Update](../../data/oledb/irowsetupdateimpl-update.md) 的 **DBROWSTATUS** 到相应的 [行状态](https://msdn.microsoft.com/en-us/library/ms722752.aspx)。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)