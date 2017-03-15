---
title: "CDataConnection::operator bool (OLE DB) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
ms.assetid: e0791faf-2ed2-4dbb-9e68-3b9b5da2b7a7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDataConnection::operator bool (OLE DB)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定当前是否举行会话。  
  
## 语法  
  
```  
  
operator bool( ) throw( );  
  
```  
  
## 备注  
 返回 `bool` \(C\+\+ 数据类型\) 的值。  表示当前会话；而**truefalse** 这意味着关闭当前会话。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDataConnection 类](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator BOOL](../../data/oledb/cdataconnection-operator-bool.md)