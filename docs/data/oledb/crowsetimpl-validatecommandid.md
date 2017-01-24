---
title: "CRowsetImpl::ValidateCommandID | Microsoft Docs"
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
  - "CRowsetImpl.ValidateCommandID"
  - "CRowsetImpl::ValidateCommandID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ValidateCommandID 方法"
ms.assetid: cdde6088-41bc-4b8f-a32b-f36f7d9b5ec0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowsetImpl::ValidateCommandID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检查任何一个或者两个 **DBID**数组是否包含字符串值，如果可用，将其复制到其数据成员和 [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)[m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。  
  
## 语法  
  
```  
  
      HRESULT CRowsetBaseImpl::ValidateCommandID(  
   DBID* pTableID,  
   DBID* pIndexID   
);  
```  
  
#### 参数  
 `pTableID`  
 \[in\] 指向表示表 . ID 的 **DBID** 的指针  
  
 `pIndexID`  
 \[in\] 对 ID. 索引表示 **DBID** 的指针  
  
## 返回值  
 标准 `HRESULT`。  
  
## 备注  
 此方法通过静态的向上转换由调用 `CRowsetImpl` 填充：，其中填充其数据成员和 [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)[m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。  默认情况下，此方法会检查或两个 **DBID**数组是否包含字符串值，如果可用，将其复制到其数据成员。  通过将与此签名的方法在 `CRowsetImpl`派生类，调用方法而不是基实现。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [CRowsetImpl 类](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)