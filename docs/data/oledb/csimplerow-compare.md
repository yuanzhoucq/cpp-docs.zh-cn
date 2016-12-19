---
title: "CSimpleRow::Compare | Microsoft Docs"
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
  - "CSimpleRow.Compare"
  - "CSimpleRow::Compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "“比较”方法"
ms.assetid: 0bb65f09-c7bc-449b-aa4e-c828cac13510
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleRow::Compare
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比较两个行，以了解它们是否引用了同一个行实例。  
  
## 语法  
  
```  
  
      HRESULT Compare(   
   CSimpleRow* pRow    
);  
```  
  
#### 参数  
 `pRow`  
 指向 `CSimpleRow` 对象的指针。  
  
## 返回值  
 通常，`HRESULT` 值 `S_OK`，指示两行显示的是同一实例，行或 **S\_FALSE**，指示两行不同。  为其他的返回值可能查看 *OLE DB 程序员参考》\) 中的*[IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx)。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [CSimpleRow 类](../../data/oledb/csimplerow-class.md)   
 [CSimpleRow::ReleaseRow](../../data/oledb/csimplerow-releaserow.md)   
 [IRowsetImpl::RefRows](../../data/oledb/irowsetimpl-refrows.md)