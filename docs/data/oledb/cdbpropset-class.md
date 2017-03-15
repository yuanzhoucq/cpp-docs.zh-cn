---
title: "CDBPropSet 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDBPropSet"
  - "ATL.CDBPropSet"
  - "ATL::CDBPropSet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBPropSet 类"
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# CDBPropSet 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从 **DBPROPIDSET** 结构继承初始化并将键字段以及 `AddPropertyIDAddProperty` 访问方法的构造函数。  
  
## 语法  
  
```  
class CDBPropSet : public tagDBPROPSET  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[AddProperty](../../data/oledb/cdbpropset-addproperty.md)|将属性添加到将属性的 ID。|  
|[CDBPropSet](../../data/oledb/cdbpropset-cdbpropset.md)|构造函数。|  
|[SetGUID](../../data/oledb/cdbpropset-setguid.md)|将 **DBPROPSET** 结构的 **guidPropertySet** 字段。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../../data/oledb/cdbpropset-operator-equal.md)|分配的一个属性 ID内容到另一个。|  
  
## 备注  
 OLE DB 提供程序和使用者使用 **DBPROPSET** 结构传递 `DBPROP` 结构数组。  每个 `DBPROP` 结构表示可以设置的单个属性。  
  
## 要求  
 **Header:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CDBPropIDSet 类](../../data/oledb/cdbpropidset-class.md)   
 [DBPROPSET Structure](https://msdn.microsoft.com/en-us/library/ms714367.aspx)   
 [DBPROP Structure](https://msdn.microsoft.com/en-us/library/ms717970.aspx)