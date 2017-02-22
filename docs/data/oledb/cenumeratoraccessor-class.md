---
title: "CEnumeratorAccessor 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CEnumeratorAccessor"
  - "CEnumeratorAccessor"
  - "ATL.CEnumeratorAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEnumeratorAccessor 类"
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CEnumeratorAccessor 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过使用 [CEnumerator](../../data/oledb/cenumerator-class.md) 访问枚举数行集合中的数据。  
  
## 语法  
  
```  
class CEnumeratorAccessor  
```  
  
## 成员  
  
### 数据成员  
  
|||  
|-|-|  
|[m\_bIsParent](../../data/oledb/cenumeratoraccessor-m-bisparent.md)|如果行是枚举数，变量指示枚举数是否是父枚举数。|  
|[m\_nType](../../data/oledb/cenumeratoraccessor-m-ntype.md)|变量指示行是否描述了数据源或枚举数。|  
|[m\_szDescription](../../data/oledb/cenumeratoraccessor-m-szdescription.md)|数据源或枚举数的描述。|  
|[m\_szName](../../data/oledb/cenumeratoraccessor-m-szname.md)|数据源或枚举数的名称。|  
|[m\_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)|传递 [IParseDisplayName](http://msdn.microsoft.com/library/windows/desktop/ms680604) 获取数据源或枚举器的名字的字符串。|  
  
## 备注  
 此行集合包括数据源和从当前枚举数的可见枚举数。  
  
## 要求  
 **Header:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)