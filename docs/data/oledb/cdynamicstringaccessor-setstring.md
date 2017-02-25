---
title: "CDynamicStringAccessor::SetString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicStringAccessor::SetString"
  - "CDynamicStringAccessor.SetString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetString 方法"
ms.assetid: 94846d8b-4c1b-47fe-acdc-1752981cee25
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# CDynamicStringAccessor::SetString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置指定列数据为字符串。  
  
## 语法  
  
```  
HRESULT SetString(  
   DBORDINAL nColumn,  
   BaseType* data  
) throw( );  
HRESULT SetString(  
   const CHAR* pColumnName,  
   BaseType* data  
) throw( );  
HRESULT SetString(  
   const WCHAR* pColumnName,  
   BaseType* data  
) throw( );  
```  
  
#### 参数  
 `nColumn`  
 \[in\] 列号。  列数以 1 开始。  特殊值 0 引用，书签列，如果中的任何一个。  
  
 `pColumnName`  
 \[in\] 为包含列名的字符串的指针。  
  
 `data`  
 \[in\] 对要写入的字符串数据的指针为指定列。  
  
## 返回值  
 设置指定列的字符串值的指针。  值的类型为 `BaseType`，是 `CHAR` 或 `WCHAR` 是 `_UNICODE` 中定义。  
  
## 备注  
 而 ANSI 字符串和第三个重写窗体接受列命名为 Unicode 字符串，第二个重写窗体接受列名。  
  
 如果 `_SECURE_ATL` 被定义具有非零值，则运行时断言失败将生成，如果输入 `data` 字符串的引用的数据列的最大大小 \(80000000\) 的长度。  否则，如果，它比最大大小 \(80000000\) 的长度，长输入字符串将被截断。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicStringAccessor 类](../../data/oledb/cdynamicstringaccessor-class.md)