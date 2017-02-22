---
title: "IOpenRowsetImpl 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IOpenRowsetImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IOpenRowsetImpl 类"
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# IOpenRowsetImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 `IOpenRowset` 接口的实现。  
  
## 语法  
  
```  
template <class SessionClass>  
class IOpenRowsetImpl : public IOpenRowset  
```  
  
#### 参数  
 `SessionClass`  
 类，从 `IOpenRowsetImpl`中派生。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[CreateRowset](../../data/oledb/iopenrowsetimpl-createrowset.md)|创建行集合对象。  未调用由用户直接。|  
|[OpenRowset](../../data/oledb/iopenrowsetimpl-openrowset.md)|打开并返回包含从一个基表或索引的所有行的行集合。\(不是 ATLDB.H\)|  
  
## 备注  
 [IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx) 接口为会话对象是必需的。  将打开并返回包含从一个基表或索引的所有行的行集合。  
  
## 要求  
 **页眉：**atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)