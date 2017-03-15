---
title: "CHAIN_PROPERTY_SET | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CHAIN_PROPERTY_SET"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHAIN_PROPERTY_SET 宏"
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CHAIN_PROPERTY_SET
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此宏链接属性组。  
  
## 语法  
  
```  
  
CHAIN_PROPERTY_SET(  
ChainClass   
)  
  
```  
  
#### 参数  
 *ChainClass*  
 \[in\] 链接属性的类的名称。  这是已包含映射的 ATL 项目向导生成的类 \(如会话、命令或数据源对象类\)。  
  
## 备注  
 可以从另一个类到您自己的类链接一个属性集合，然后直接从类访问属性。  
  
> [!CAUTION]
>  慎重使用此宏。  不正确的使用可能导致使用者在 OLE DB 一致性测试失败。  
  
## 要求  
 **标头：** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)