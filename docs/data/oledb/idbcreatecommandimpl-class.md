---
title: "IDBCreateCommandImpl 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IDBCreateCommandImpl"
  - "IDBCreateCommandImpl"
  - "ATL.IDBCreateCommandImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDBCreateCommandImpl 类"
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IDBCreateCommandImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供接口的实现。[IDBCreateCommand](https://msdn.microsoft.com/en-us/library/ms711625.aspx)  
  
## 语法  
  
```  
template <class T, class CommandClass >  
class ATL_NO_VTABLE IDBCreateCommandImpl   
   : public IDBCreateCommand  
```  
  
#### 参数  
 `T`  
 从 `IDBCreateCommandImpl`派生的会话对象。  
  
 `CommandClass`  
 命令类。  
  
## 成员  
  
### 接口方法  
  
|||  
|-|-|  
|[CreateCommand](../../data/oledb/idbcreatecommandimpl-createcommand.md)|创建新命令。|  
  
## 备注  
 在获取一个新命令的会话对象的可选接口。  
  
## 要求  
 **页眉：**atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)