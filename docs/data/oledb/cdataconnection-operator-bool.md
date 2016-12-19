---
title: "CDataConnection::operator BOOL | Microsoft Docs"
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
  - "CDataConnection::operatorBOOL"
  - "ATL::CDataConnection::operatorBOOL"
  - "CDataConnection.operatorBOOL"
  - "ATL.CDataConnection.operatorBOOL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BOOL 运算符"
  - "运算符 bool"
ms.assetid: ad0bea7f-61ff-47f7-8127-32a31e3e9b9d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::operator BOOL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定当前是否举行会话。  
  
## 语法  
  
```  
  
operator BOOL( ) throw( );  
  
```  
  
## 备注  
 返回 **BOOL** \(MFC typedef\) 值。  表示当前会话；而**TRUE FALSE** 这意味着关闭当前会话。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDataConnection 类](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator bool](../../data/oledb/cdataconnection-operator-bool-ole-db.md)