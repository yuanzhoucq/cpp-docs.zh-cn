---
title: "IRowsetChangeImpl::FlushData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetChangeImpl::FlushData"
  - "IRowsetChangeImpl.FlushData"
  - "FlushData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FlushData 方法"
ms.assetid: fd4bc73b-bc25-4aab-90d5-0bed92670c88
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetChangeImpl::FlushData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

被目标的数据提供程序的 Overidden 到的存储。  
  
## 语法  
  
```  
  
      HRESULT FlushData(  
   HROW hRowToFlush,  
   HACCESSOR hAccessorToFlush   
);  
```  
  
#### 参数  
 *hRowToFlush*  
 \[in\] 对行句柄数据。  此行类型从 `IRowsetImpl` 类 \(`CSimpleRow` 的 *RowClass* 模板参数确定的默认方法。\)  
  
 *hAccessorToFlush*  
 \[in\] 为访问器中处理，包含信息和约束类型信息。其 **PROVIDER\_MAP** \(请参见 [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)\)。  
  
## 返回值  
 标准 `HRESULT`。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IRowsetChangeImpl 类](../../data/oledb/irowsetchangeimpl-class.md)