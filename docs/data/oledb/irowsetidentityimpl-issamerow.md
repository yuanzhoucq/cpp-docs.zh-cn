---
title: "IRowsetIdentityImpl::IsSameRow | Microsoft Docs"
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
  - "IsSameRow"
  - "IRowsetIdentityImpl.IsSameRow"
  - "ATL.IRowsetIdentityImpl.IsSameRow"
  - "IRowsetIdentityImpl::IsSameRow"
  - "ATL::IRowsetIdentityImpl::IsSameRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsSameRow 方法"
ms.assetid: e35ad54e-73f1-4dc0-8d8c-9e98202baf0a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetIdentityImpl::IsSameRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比较两行柄以查看其是否引用同一行。  
  
## 语法  
  
```  
  
      STDMETHOD( IsSameRow )(  
   HROW hThisRow,  
   HROW hThatRow   
);  
```  
  
#### 参数  
 参阅《*OLE DB 程序员参考》\) 中的* 中的 [IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx)。  
  
## 备注  
 若要比较行句柄，该方法将 **HROW** 转换句柄并调用 **RowClass** 成员的指针上的 `memcmp`。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IRowsetIdentityImpl 类](../../data/oledb/irowsetidentityimpl-class.md)