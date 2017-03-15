---
title: "BLOB_NAME_STATUS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BLOB_NAME_STATUS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BLOB_NAME_STATUS 宏"
ms.assetid: 4564e4a0-8e5e-436a-bd1e-012d2a1b8642
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# BLOB_NAME_STATUS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于使用 `BEGIN_COLUMN_MAP` 和 `END_COLUMN_MAP` 绑定二进制大对象 \([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)\)。  类似于 [BLOB\_NAME](../../data/oledb/blob-name.md)，除此之外，此宏还获取 BLOB 数据列的状态。  
  
## 语法  
  
```  
  
BLOB_NAME_STATUS(  
pszName  
,   
IID  
,   
flags  
,   
data  
, status )  
```  
  
#### 参数  
 `pszName`  
 \[in\] 为列名的指针。  名称必须是一个 Unicode 字符串。  例如可以通过放置一个"左”Finalize 此名称，在前面：`L"MyColumn"`。  
  
 *IID*  
 \[in\] 连接 GUID，如 **IDD\_ISequentialStream**，用于检索 BLOB。  
  
 `flags`  
 \[in\] 存储标志模式所定义的 OLE 结构化存储模型 \(例如，**STGM\_READ**。\)  
  
 `data`  
 \[in\] 用户记录的相应数据成员。  
  
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
 [BLOB\_NAME\_LENGTH\_STATUS](../../data/oledb/blob-name-length-status.md)