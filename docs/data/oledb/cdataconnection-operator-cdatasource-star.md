---
title: "CDataConnection::operator CDataSource* | Microsoft Docs"
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
  - "CDataSource*"
  - "CDataConnection::operatorCDataSource*"
  - "CDataConnection.operatorCDataSource*"
  - "operatorCDataSource*"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataSource* 运算符"
  - "运算符 * (CDataSource)"
ms.assetid: 9118e324-e68d-45c5-a791-03f041d420ed
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::operator CDataSource*
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回包含的`CDataSource` 对象的指针。  
  
## 语法  
  
```  
  
operator const CDataSource*() throw( );  
  
```  
  
## 备注  
 此运算符返回指向包含的 `CDataSource` 对象，允许您通过 `CDataSource` 指针所需的 `CDataConnection` 对象。  
  
 提供用法示例参见 [运算符并&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDataConnection 类](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)