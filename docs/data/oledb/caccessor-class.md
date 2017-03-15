---
title: "CAccessor 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CAccessor<T>"
  - "ATL::CAccessor"
  - "CAccessor"
  - "ATL::CAccessor<T>"
  - "ATL.CAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccessor 类"
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CAccessor 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示某个访问器类型。  
  
## 语法  
  
```  
  
      template < class   
      T  
       >  
class CAccessor : public CAccessorBase, public T  
```  
  
#### 参数  
 `T`  
 用户记录类。  
  
## 备注  
 当您将它记录静态绑定到数据源时，请使用。  记录包含缓冲区。  此类支持行集合上具有多个访问器。  
  
 在结构和已知的数据库类型时，请使用此种访问器类型。  
  
 如果访问器包含指向必须释放内存的字段 \(如 `BSTR` 或接口\)，请调用成员函数 [CAccessorRowset::FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md)，下一记录前读取。  
  
## 要求  
 **页眉：**atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)