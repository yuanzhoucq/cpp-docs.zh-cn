---
title: "CDBPropIDSet 类 | Microsoft Docs"
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
  - "CDBPropIDSet"
  - "ATL.CDBPropIDSet"
  - "ATL::CDBPropIDSet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBPropIDSet 类"
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBPropIDSet 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从 **DBPROPIDSET** 结构继承初始化并将键字段以及 [AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md) 访问方法的构造函数。  
  
## 语法  
  
```  
class CDBPropIDSet : public tagDBPROPIDSET  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)|将属性添加到将属性的 ID。|  
|[CDBPropIDSet](../../data/oledb/cdbpropidset-cdbpropidset.md)|构造函数。|  
|[SetGUID](../../data/oledb/cdbpropidset-setguid.md)|设置属性的 ID 的 GUID。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../../data/oledb/cdbpropidset-operator-equal.md)|分配的一个属性 ID内容到另一个。|  
  
## 备注  
 OLE DB 使用者使用 **DBPROPIDSET** 结构传递数组使用者要获取属性信息的属性 ID。  在 [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) 一个结构中标识的属性属于一属性。  
  
## 要求  
 **Header:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)