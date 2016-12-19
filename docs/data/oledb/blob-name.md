---
title: "BLOB_NAME | Microsoft Docs"
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
  - "BLOB_NAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BLOB_NAME 宏"
ms.assetid: 757acd0d-946d-447d-937e-94ecd700ba38
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BLOB_NAME
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于使用 `BEGIN_COLUMN_MAP` 和 `END_COLUMN_MAP` 绑定二进制大对象 \([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)\)。  类似于 [BLOB\_ENTRY](../../data/oledb/blob-entry.md)，除此之外，此宏使用列名代替列数。  
  
## 语法  
  
```  
  
BLOB_NAME(  
pszName  
,   
IID  
,   
flags  
,   
data )  
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
  
## 示例  
 参见 [如何才能检索 BLOB?](../../data/oledb/retrieving-a-blob.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB\_NAME\_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB\_NAME\_LENGTH\_STATUS](../../data/oledb/blob-name-length-status.md)   
 [BLOB\_NAME\_STATUS](../../data/oledb/blob-name-status.md)