---
title: "BLOB_ENTRY | Microsoft Docs"
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
  - "BLOB_ENTRY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BLOB_ENTRY 宏"
ms.assetid: 89e40678-0869-49ed-b502-0fa2630a9081
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BLOB_ENTRY
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于使用 `BEGIN_COLUMN_MAP` 和 `END_COLUMN_MAP` 绑定二进制大对象 \([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)\)。  
  
## 语法  
  
```  
  
BLOB_ENTRY(  
nOrdinal  
,  
 IID  
,   
flags  
,   
data  
 )  
  
```  
  
#### 参数  
 `nOrdinal`  
 \[in\] 列号。  
  
 *IID*  
 \[in\] 连接 GUID，如 **IDD\_ISequentialStream**，用于检索 BLOB。  
  
 `flags`  
 \[in\] 存储标志模式所定义的 OLE 结构化存储模型 \(例如，**STGM\_READ**。\)  
  
 `data`  
 \[in\] 用户记录的相应数据成员。  
  
## 示例  
 参见 [如何才能检索 BLOB?](../../data/oledb/retrieving-a-blob.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB\_ENTRY\_LENGTH](../../data/oledb/blob-entry-length.md)   
 [BLOB\_ENTRY\_LENGTH\_STATUS](../../data/oledb/blob-entry-length-status.md)   
 [BLOB\_ENTRY\_STATUS](../../data/oledb/blob-entry-status.md)