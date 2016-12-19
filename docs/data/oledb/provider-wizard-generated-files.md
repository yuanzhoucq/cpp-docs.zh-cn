---
title: "提供程序向导生成的文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供程序, 向导生成的文件"
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 提供程序向导生成的文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“ATL OLE DB 提供程序向导”生成以下文件。  以下主题采用简称“MyProvider”，但确切的文件名取决于您在创建提供程序时所做的选择。  
  
|文件名|说明|  
|---------|--------|  
|MyProviderRS.cpp|包含命令帮助器 `Execute` 方法和提供程序列映射。|  
|MyProviderDS.h|实现数据源对象。  该头文件包含数据源属性的属性映射。|  
|MyProviderRS.h|实现命令和行集合对象。  该头文件包含行集合和命令属性的属性映射。|  
|MyProviderSess.h|实现会话对象。  该头文件包含会话属性的属性映射。|  
|MyProvider.rgs|包含“OLE DB 提供程序向导”生成的注册对象|  
  
## 请参阅  
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)