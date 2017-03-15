---
title: "CAccessorBase 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CAccessorBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccessorBase 类"
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CAccessorBase 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 模板的所有访问器从该类派生。  `CAccessorBase` 允许某一行集合管理多个访问器。  它还为参数和输出列的绑定。  
  
## 语法  
  
```  
// Replace with syntax  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[关闭](../../data/oledb/caccessorbase-close.md)|关闭访问器。|  
|[GetHAccessor](../../data/oledb/caccessorbase-gethaccessor.md)|检索访问器处理。|  
|[GetNumAccessors](../../data/oledb/caccessorbase-getnumaccessors.md)|检索类创建访问器的数量。|  
|[IsAutoAccessor](../../data/oledb/caccessorbase-isautoaccessor.md)|测试指定的访问器是否为自动访问器。|  
|[ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md)|版本访问器。|  
  
## 要求  
 **Header:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)