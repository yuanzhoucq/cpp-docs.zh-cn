---
title: "CRowsetImpl::GetCommandFromID | Microsoft Docs"
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
  - "CRowsetImpl::GetCommandFromID"
  - "GetCommandFromID"
  - "CRowsetImpl.GetCommandFromID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCommandFromID 方法"
ms.assetid: 9f39cb07-1c40-486f-ba5b-cb4a65fab8a7
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowsetImpl::GetCommandFromID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检查任何一个或者两个参数是否包含字符串值，如果可用，将字符串值转换为数据成员和 [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。  
  
## 语法  
  
```  
  
      HRESULT CRowsetBaseImpl::GetCommandFromID(  
   DBID* pTableID,  
   DBID* pIndexID   
);  
```  
  
#### 参数  
 `pTableID`  
 \[in\] 指向表示表 . ID 的 **DBID** 的指针  
  
 `pIndexID`  
 \[in\] 指向表示Inde ID 的 **DBID** 的指针  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 此方法通过静态的向上转换由调用 `CRowsetImpl` 填充：，其中填充数据成员和 [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。  默认情况下，此方法会检查或两个参数是否包含字符串值。  如果包含的字符串值，此方法复制指向数据成员的字符串值。  通过将与此签名的方法在 `CRowsetImpl`派生类，调用方法而不是基实现。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [CRowsetImpl 类](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)