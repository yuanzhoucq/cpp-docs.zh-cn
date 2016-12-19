---
title: "CNoAccessor 类 | Microsoft Docs"
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
  - "ATL::CNoAccessor"
  - "CNoAccessor"
  - "ATL.CNoAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNoAccessor 类"
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CNoAccessor 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以用作模板参数 \(`TAccessor`\)。模板类，如 `CCommand` 和 `CTable`，需要访问器类参数。  
  
## 语法  
  
```  
class CNoAccessor  
```  
  
## 备注  
 当不希望类支持参数或输出列时，请将 `CNoAccessor` 用作模板参数。  
  
 `CNoAccessor` 执行以下存根方法，每个对应于其他任何访问器类方法：  
  
-   \- 对**BindColumns** 访问函数的绑定列。  
  
-   `BindParameters` \- 绑定到列创建的参数。  
  
-   **绑定** \- 创建绑定。  
  
-   关闭**关闭** \- 访问器。  
  
-   `ReleaseAccessors` 类 \- 版本创建访问器。  
  
-   `FreeRecordMemory` \- 版本需要释放在当前记录的所有列。  
  
-   `GetColumnInfo` \- 从已打开的行集合获取列信息。  
  
-   `GetNumAccessors` \- 检索类创建访问器的数量。  
  
-   `IsAutoAccessor` \- 返回 true，则访问器自动检索数据。在移动操作时。  
  
-   `GetHAccessor` \- 检索指定访问器的访问器处理。  
  
-   `GetBuffer` \- 检索指向书签缓冲区。  
  
-   **NoBindOnNullRowset** \- 阻止在空行集的数据绑定。  
  
## 要求  
 **页眉：**atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)