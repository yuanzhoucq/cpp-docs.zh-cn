---
title: "CDataConnection::CDataConnection | Microsoft Docs"
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
  - "CDataConnection.CDataConnection"
  - "ATL.CDataConnection.CDataConnection"
  - "CDataConnection::CDataConnection"
  - "ATL::CDataConnection::CDataConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataConnection 类, 构造函数"
ms.assetid: ac25c9a0-44d3-4083-b13f-76c07772e12d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::CDataConnection
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实例化和初始化 `CDataConnection` 对象。  
  
## 语法  
  
```  
  
      CDataConnection();   
CDataConnection(  
   const CDataConnection &ds  
);  
```  
  
#### 参数  
 `ds`  
 \[in\] 与现有数据连接上的引用复制。  
  
## 备注  
 第一种替代方法将创建具有默认设置的新 `CDataConnection` 对象。  
  
 第二个重写的设置创建的新 `CDataConnection` 对象存在指定的数据连接对象。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDataConnection 类](../../data/oledb/cdataconnection-class.md)