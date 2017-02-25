---
title: "IRowsetChangeImpl::SetData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetData"
  - "IRowsetChangeImpl::SetData"
  - "ATL.IRowsetChangeImpl.SetData"
  - "IRowsetChangeImpl.SetData"
  - "ATL::IRowsetChangeImpl::SetData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetData 方法"
ms.assetid: 81e1dd0a-0518-440c-8808-cee76e4929c7
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IRowsetChangeImpl::SetData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置一行中的一列或多列中的数据值。  
  
## 语法  
  
```  
  
      STDMETHOD ( SetData )(  
   HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData   
);  
```  
  
#### 参数  
 请参见 [IRowsetChange::SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx)在 *OLE DB编程* 中。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetChangeImpl 类](../../data/oledb/irowsetchangeimpl-class.md)