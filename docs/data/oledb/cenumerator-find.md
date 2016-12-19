---
title: "CEnumerator::Find | Microsoft Docs"
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
  - "CEnumerator::Find"
  - "ATL::CEnumerator::Find"
  - "ATL.CEnumerator.Find"
  - "CEnumerator.Find"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Find 方法"
ms.assetid: 69a153af-d6c3-40fd-9018-27c7d2f344c6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CEnumerator::Find
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在找到可用提供程序中的指定名称。  
  
## 语法  
  
```  
  
      bool Find(   
   TCHAR* szSearchName    
) throw( );  
```  
  
#### 参数  
 *szSearchName*  
 \[in\] 要搜索的名称。  
  
## 返回值  
 如果找到名字，则为**true**。  否则为 **false**。  
  
## 备注  
 到 [ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) 的 **SOURCES\_NAME** 成员的这一映射名称连接。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CEnumerator 类](../../data/oledb/cenumerator-class.md)