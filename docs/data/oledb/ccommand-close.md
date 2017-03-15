---
title: "CCommand::Close | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CCommand.Close"
  - "CCommand::Close"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Close 方法"
ms.assetid: 4da9c02c-7082-4e47-a0fa-78b546f0f7d2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CCommand::Close
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

发布与命令关联的访问器 行集。  
  
## 语法  
  
```  
void Close( );  
```  
  
## 备注  
 命令使用一行集、结果集访问器和 \(可选的\) 参数访问器 \(不同于不支持参数及不需要参数访问器的表\)。  
  
 当执行命令，还应在命令之后调用 `Close` 和 [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)。  
  
 在要重复执行同一命令时，您应在调用 `Execute`之前通过调用 `Close` 释放每个结果集访问器。  在序列末尾，应调用 `ReleaseCommand` 释放参数访问器。  另一种常见情形是调用具有输出参数的存储过程。  对于许多提供程序 \(如 SQL Server 的 OLE DB 提供程序\) 输出参数值将不可访问，直到您关闭结果集访问器。  调用 `Close` 关闭返回的行集和结果集访问器，而不是参数访问器，从而允许检索输出参数值。  
  
## 示例  
 下面的示例说明了当重复执行同一命令时如何能够调用 `Close` 和 `ReleaseCommand`.  
  
 [!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/CPP/ccommand-close_1.cpp)]  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)   
 [CCommand::ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)