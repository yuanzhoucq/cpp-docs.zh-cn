---
title: "CRestrictions 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CRestrictions"
  - "CRestrictions"
  - "ATL.CRestrictions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRestrictions 类"
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# CRestrictions 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可用于架构行集指定绑定的泛型类。  
  
## 语法  
  
```  
template <   
   class T,   
   short nRestrictions,   
   const GUID* pguid   
>  
class CRestrictions : public CSchemaRowset <   
   T,   
   nRestrictions   
>  
```  
  
#### 参数  
 `T`  
 用于访问器的类。  
  
 `nRestrictions`  
 限制列的数量架构行集合中。  
  
 `pguid`  
 设置为 GUID 的指针的架构。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[打开](../../data/oledb/crestrictions-open.md)|根据用户提供的限制返回结果集。|  
  
## 要求  
 **头文件：**atldbsch.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)