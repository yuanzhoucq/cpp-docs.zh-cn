---
title: "CBookmark 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CBookmark"
  - "ATL::CBookmark<nSize>"
  - "CBookmark"
  - "ATL.CBookmark<nSize>"
  - "ATL::CBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBookmark 类"
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CBookmark 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示在其缓冲区中书签的值。  
  
## 语法  
  
```  
template < DBLENGTH nSize = 0 >  
class CBookmark : public CBookmarkBase  
template < >  
class CBookmark< 0 > : public CBookmarkBase  
```  
  
#### 参数  
 `nSize`  
 书签缓冲区的大小 \(以字节为单位\)。  当 `nSize` 为零，书签缓冲区将在运行时动态创建的。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[CBookmark](../../data/oledb/cbookmark-class.md)|构造函数|  
|[GetBuffer](../../data/oledb/cbookmark-getbuffer.md)|检索指向缓冲区。|  
|[GetSize](../../data/oledb/cbookmark-getsize.md)|检索以字节缓冲区的大小。|  
|[SetBookmark](../../data/oledb/cbookmark-setbookmark.md)|设置书签值。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../../data/oledb/cbookmark-operator-equal.md)|将一个 `CBookmark` 类添加到另一个。|  
  
## 备注  
 **CBookmark\<0\>** 是 `CBookmark`模板的专用化；其缓冲区在运行时动态创建的。  
  
## 要求  
 **页眉：**atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)