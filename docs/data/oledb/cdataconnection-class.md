---
title: "CDataConnection 类 | Microsoft Docs"
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
  - "ATL::CDataConnection"
  - "ATL.CDataConnection"
  - "CDataConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataConnection 类"
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理与数据源的连接。  
  
## 语法  
  
```  
class CDataConnection  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[CDataConnection](../../data/oledb/cdataconnection-cdataconnection.md)|构造函数。  实例化和初始化 `CDataConnection` 对象。|  
|[复制](../../data/oledb/cdataconnection-copy.md)|创建现有数据连接的副本。|  
|[打开](../../data/oledb/cdataconnection-open.md)|使用初始化字符串打开与数据源的连接。|  
|[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)|开始当前连接的新会话。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符 BOOL](../../data/oledb/cdataconnection-operator-bool.md)|确定当前是否举行会话。|  
|[operator bool](../../data/oledb/cdataconnection-operator-bool-ole-db.md)|确定当前是否举行会话。|  
|[运算符 CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)|返回对创建的 `CDataSource` 容器的引用。|  
|[运算符 CDataSource\*](../../data/oledb/cdataconnection-operator-cdatasource-star.md)|返回包含的`CDataSource` 对象的指针。|  
|[运算符 CSession&&](../../data/oledb/cdataconnection-operator-csession-amp.md)|返回对创建的 `CSession` 容器的引用。|  
|[运算符 CSession\*](../../data/oledb/cdataconnection-operator-csession-star.md)|返回包含的`CSession` 对象的指针。|  
  
## 备注  
 `CDataConnection` 是创建客户端的一种有用类封装，因为它需要所需完成，则连接到数据源后 \(数据源和会话\) 和某些工作  
  
 如果没有 `CDataConnection`，您必须创建一个 `CDataSource` 对象，则调用其方法 [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) [CSession](../../data/oledb/csession-class.md)，然后创建对象的实例，调用其方法 [CCommand](../../data/oledb/ccommand-class.md) [打开](../../data/oledb/csession-open.md)，然后创建对象并调用其方法。**打开**\*  
  
 `CDataConnection`，需要创建连接对象，只传递它初始化字符串，然后使用将打开命令的该连接。  如果上重复使用计划到数据库的连接时，最好保持连接打开，因此，`CDataConnection` 提供了一种简便方式执行此操作。  
  
> [!NOTE]
>  如果您创建需要处理多个会话的数据库应用程序，需要将使用 [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)