---
title: "CEnumerator 类 | Microsoft Docs"
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
  - "CEnumerator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEnumerator 类"
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CEnumerator 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 OLE DB 枚举器对象，揭露了[ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) 接口返回一个描述任何数据源和枚举器的行集合。  
  
## 语法  
  
```  
class CEnumerator :   
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[查找](../../data/oledb/cenumerator-find.md)|通过可用的提供者（数据源）搜索查找具有指定名称的一个。|  
|[GetMoniker](../../data/oledb/cenumerator-getmoniker.md)|为当前记录检索 `IMoniker` 接口。|  
|[打开](../../data/oledb/cenumerator-open.md)|打开枚举器。|  
  
## 备注  
 可以从此类间接检索 **ISourcesRowset** 数据。  
  
## 要求  
 **Header:**atldbcli.h  
  
## 请参阅  
 [DBViewer](../../top/visual-cpp-samples.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)