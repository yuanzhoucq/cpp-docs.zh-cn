---
title: "IRowsetUpdateImpl::SetData | Microsoft Docs"
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
  - "IRowsetUpdateImpl::SetData"
  - "IRowsetUpdateImpl.SetData"
  - "ATL::IRowsetUpdateImpl::SetData"
  - "ATL.IRowsetUpdateImpl.SetData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetData 方法"
ms.assetid: 7288a8d1-a7cf-4957-b832-0f3b18fd0da4
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetUpdateImpl::SetData
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
  
## 备注  
 此方法将重写方法 [IRowsetChangeImpl::SetData](../../data/oledb/irowsetchangeimpl-setdata.md)，但包括原始数据缓存允许立即执行和延迟的处理操作。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)