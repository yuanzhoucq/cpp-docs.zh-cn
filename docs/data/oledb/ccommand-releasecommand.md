---
title: "CCommand::ReleaseCommand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CCommand.ReleaseCommand"
  - "ReleaseCommand"
  - "CCommand::ReleaseCommand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseCommand 方法"
ms.assetid: 3b58230c-13d5-45c5-b43e-bb013ecc3019
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CCommand::ReleaseCommand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

释放参数访问器，然后释放命令。  
  
## 语法  
  
```  
  
void CCommandBase::ReleaseCommand( ) throw( );  
  
```  
  
## 备注  
 `ReleaseCommand`与**关闭**一起使用。  参见 [关闭](../../data/oledb/ccommand-close.md) 有关用法详细信息。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)   
 [CCommand::Close](../../data/oledb/ccommand-close.md)