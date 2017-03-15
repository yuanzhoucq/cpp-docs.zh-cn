---
title: "CAccessorBase::ReleaseAccessors | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CAccessorBase::ReleaseAccessors"
  - "CAccessorBase.ReleaseAccessors"
  - "ReleaseAccessors"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseAccessors 方法"
ms.assetid: f08bc88e-0552-4a9c-9c65-b4061094649a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CAccessorBase::ReleaseAccessors
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

释放类创建访问器。  
  
## 语法  
  
```  
  
      HRESULT ReleaseAccessors(  
   IUnknown* pUnk   
);  
```  
  
#### 参数  
 *pUnk*  
 \[in\] 为 **IUnknown** 接口的指针访问器创建的 COM 对象。  
  
## 返回值  
 标准 `HRESULT`。  
  
## 备注  
 从 [CAccessorRowset::Close](../../data/oledb/caccessorrowset-close.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CAccessorBase 类](../../data/oledb/caccessorbase-class.md)