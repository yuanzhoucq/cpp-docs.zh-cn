---
title: "CDynamicStringAccessor::GetString | Microsoft Docs"
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
  - "CDynamicStringAccessor.GetString"
  - "CDynamicStringAccessor::GetString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetString 方法"
ms.assetid: 4af27f27-7589-49f5-93d8-6ef05c023c8a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicStringAccessor::GetString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

恢复检索指定列数据为字符串。  
  
## 语法  
  
```  
  
      BaseType* GetString(  
   DBORDINAL nColumn  
) const throw( );  
BaseType* GetString(  
   const CHAR* pColumnName  
) const throw( );  
BaseType* GetString(  
   const WCHAR* pColumnName  
) const throw( );  
```  
  
#### 参数  
 `nColumn`  
 \[in\] 列号。  列数以 1 开始。  若有的话，值 0 是指书签列。  
  
 `pColumnName`  
 \[in\] 为包含列名的字符串的指针。  
  
## 返回值  
 为检索指定列中字符串值的指针。  ***BaseType*** 类型的值依赖于\_UNICODE 是否定义，它将是 **CHAR** 或 **WCHAR** 。  如果指定的列未找到，返回 NULL。  
  
## 备注  
 第二个重写窗体将列命名视为 ANSI 字符串。  第三个重写窗体接受列名作为 Unicode 字符串。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicStringAccessor 类](../../data/oledb/cdynamicstringaccessor-class.md)