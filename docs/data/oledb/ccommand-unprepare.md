---
title: "CCommand::Unprepare | Microsoft Docs"
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
  - "Unprepare"
  - "CCommand.Unprepare"
  - "CCommand::Unprepare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unprepare 方法"
ms.assetid: 4fe59988-fe51-4c7c-a156-72b68e3d642b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCommand::Unprepare
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

放弃当前命令执行计划。  
  
## 语法  
  
```  
  
HRESULT CCommandBase::Unprepare( ) throw( );  
  
```  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 此方法包装 OLE DB 方法 [ICommandPrepare::Unprepare](https://msdn.microsoft.com/en-us/library/ms719635.aspx)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)