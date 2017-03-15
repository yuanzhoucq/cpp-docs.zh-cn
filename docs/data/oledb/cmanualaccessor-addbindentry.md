---
title: "CManualAccessor::AddBindEntry | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CManualAccessor::AddBindEntry"
  - "ATL.CManualAccessor.AddBindEntry"
  - "CManualAccessor::AddBindEntry"
  - "AddBindEntry"
  - "CManualAccessor.AddBindEntry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddBindEntry 方法"
ms.assetid: 8556dda9-dda1-4f67-96bc-6031e6c6a271
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CManualAccessor::AddBindEntry
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

添加输入绑定到输出列。  
  
## 语法  
  
```  
  
      void AddBindEntry(  
   DBORDINAL nOrdinal,  
   DBTYPE wType,  
   DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL   
) throw ( );  
```  
  
#### 参数  
 请参阅在*OLE DB Programmer's Reference* 中 [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 `nOrdinal`  
 \[in\] 列号。  
  
 `wType`  
 \[in\] 数据类型  
  
 `nColumnSize`  
 \[in\] 列大小 \(以字节为单位\)。  
  
 `pData`  
 \[in\] 到缓冲区中存储的数据的指针。  
  
 `pLength`  
 如果需要的话 \[in\] 为字段长度的指针。  
  
 `pStatus`  
 \[in\] 绑定到变量的指针到列状态，如果必须。  
  
## 备注  
 若要使用此功能，必须首先调用 [CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)。  您与 `CreateAccessor`中指定的列数无法添加更多项。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)   
 [DBViewer 示例](../../top/visual-cpp-samples.md)