---
title: "IRowsetUpdateImpl::Update | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IRowsetUpdateImpl::Update"
  - "IRowsetUpdateImpl::Update"
  - "IRowsetUpdateImpl.Update"
  - "ATL.IRowsetUpdateImpl.Update"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Update 方法"
ms.assetid: 9ec6884d-aa9c-4871-a803-c048f162403c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetUpdateImpl::Update
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

传输进行的任何更改。行，因为最后获取或更新。  
  
## 语法  
  
```  
  
      STDMETHOD ( Update )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus   
);  
```  
  
#### 参数  
 `hReserved`  
 \[in\] 对应于[IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)中的 `hChapter` 参数。  
  
 有关其他参数，请参阅*OLE DB 程序员参考手册*中的[IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)。  
  
## 备注  
 通过更改调用 [IRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)传输。  使用者必须 \+ 要使更改生效。调用 [CRowset::Update](../../data/oledb/crowset-update.md)。  设置 *prgRowstatus* 为相应值如 *OLE DB 程序员参考》\) 中的*[行状态](https://msdn.microsoft.com/en-us/library/ms722752.aspx) 所述。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)