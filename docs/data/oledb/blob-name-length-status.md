---
title: "BLOB_NAME_LENGTH_STATUS | Microsoft Docs"
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
  - "BLOB_NAME_LENGTH_STATUS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BLOB_NAME_LENGTH_STATUS 宏"
ms.assetid: 3cc3ec8d-80a5-4522-848a-123fcaee58cb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BLOB_NAME_LENGTH_STATUS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Used with `BEGIN_COLUMN_MAP` and `END_COLUMN_MAP` to bind a binary large object \([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)\).  Similar to [BLOB\_NAME](../../data/oledb/blob-name.md), except that this macro also gets the length and status of the BLOB data column.  
  
## 语法  
  
```  
  
BLOB_NAME_LENGTH_STATUS(  
pszName  
,   
IID  
,   
flags  
,   
data  
,   
length  
, status )  
```  
  
#### 参数  
 `pszName`  
 \[in\] 为列名的指针。  名称必须是一个 Unicode 字符串。  例如可以通过放置一个 'L'在名称前面，例如：`L"MyColumn"`。  
  
 *IID*  
 \[in\] 连接 GUID，如 **IDD\_ISequentialStream**，用于检索 BLOB。  
  
 `flags`  
 \[in\] 存储标志模式所定义的 OLE 结构化存储模型 \(例如，**STGM\_READ**。\)  
  
 `data`  
 \[in\] 用户记录的相应数据成员。  
  
 *length*  
 \[out\] \(实际\) BLOB 列的字节的长度。  
  
 *status*  
 \[out\] BLOB字段的状态。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB\_NAME](../../data/oledb/blob-name.md)   
 [BLOB\_NAME\_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB\_NAME\_STATUS](../../data/oledb/blob-name-status.md)