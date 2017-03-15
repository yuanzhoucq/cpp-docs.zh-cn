---
title: "CStreamRowset 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CStreamRowset<TAccessor>"
  - "ATL::CStreamRowset"
  - "CStreamRowset"
  - "ATL.CStreamRowset<TAccessor>"
  - "ATL.CStreamRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStreamRowset 类"
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# CStreamRowset 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 `CCommand` 或 `CTable`。  
  
## 语法  
  
```  
template <class TAccessor = CAccessorBase>  
class CStreamRowset  
```  
  
#### 参数  
 `TAccessor`  
 一个访问器类  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[CStreamRowset](../../data/oledb/cstreamrowset-cstreamrowset.md)|构造函数。  实例化和初始化 `CStreamRowset` 对象。|  
|[关闭](../../data/oledb/cstreamrowset-close.md)|释放类中的接口指针。[ISequentialStream](https://msdn.microsoft.com/en-us/library/ms718035.aspx)|  
  
## 备注  
 例如使用 `CStreamRowset` 在 `CCommand` 或 `CTable` 中，声明：  
  
 [!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/CPP/cstreamrowset-class_1.cpp)]  
  
 或  
  
 [!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/CPP/cstreamrowset-class_2.cpp)]  
  
 `ICommand::Execute` 返回一个 `ISequentialStream` 指针，该指针存储在 `m_spStream`中。  然后，您可以使用 **Read** 方法检索 XML 格式的（Unicode 字符串）数据。  例如：  
  
 [!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/CPP/cstreamrowset-class_3.cpp)]  
  
 SQL Server 2000 执行 XML 格式化，并将行集合的所有列和所有行作为一个 XML 字符串返回。  
  
> [!NOTE]
>  此功能仅适用于 SQL Server 2000 一起使用。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)