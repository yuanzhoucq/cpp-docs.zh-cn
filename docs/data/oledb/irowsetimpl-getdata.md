---
title: "IRowsetImpl::GetData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IRowsetImpl.GetData"
  - "ATL::IRowsetImpl::GetData"
  - "IRowsetImpl::GetData"
  - "IRowsetImpl.GetData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetData 方法 [OLE DB]"
ms.assetid: cb15f1cc-bd25-4b74-93c3-db71aa93829c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetImpl::GetData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从行的行集合副本中检索数据。  
  
## 语法  
  
```  
  
      STDMETHOD( GetData )(  
   HROW hRow,  
   HACCESSOR hAccessor,  
   void* pDstData   
);  
```  
  
#### 参数  
 参阅《*OLE DB 程序员参考》\) 中的*[IRowset::GetData](https://msdn.microsoft.com/en-us/library/ms716988.aspx)。  
  
 有些参数对应于 *OLE DB 程序员参考* 不同的名称的引用参数在 **IRowset::GetData**中说明：  
  
|OLE DB 模板参数|*OLE DB 程序员的引用参数*|  
|-----------------|-----------------------|  
|*pDstData*|`pData`|  
  
## 备注  
 使用 OLE DB 数据转换 DLL，并处理数据转换。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)