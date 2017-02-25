---
title: "BEGIN_PROPERTY_SET_EX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BEGIN_PROPERTY_SET_EX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_PROPERTY_SET_EX 宏"
ms.assetid: c95e7fab-edce-47b8-b282-200e53a2ea8a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# BEGIN_PROPERTY_SET_EX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

标记的属性集的开头。属性集映射。  
  
## 语法  
  
```  
  
BEGIN_PROPERTY_SET_EX(  
guid  
, flags )  
```  
  
#### 参数  
 `guid`  
 \[in\] 属性的 GUID。  
  
 `flags`  
 \[in\] 不需要公开的属性集的公开属性的提供程序。**UPROPSET\_HIDDEN** 或 **UPROPSET\_PASSTHROUGH** 定义在提供程序的范围。  
  
## 示例  
 参见 [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md)。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)