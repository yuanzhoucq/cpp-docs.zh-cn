---
title: "CXMLAccessor 类 | Microsoft Docs"
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
  - "ATL::CXMLAccessor"
  - "CXMLAccessor"
  - "ATL.CXMLAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CXMLAccessor 类"
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CXMLAccessor 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以访问数据源以字符串数据，在您不了解数据存储区的架构 \(基础结构\)。  
  
## 语法  
  
```  
class CXMLAccessor : public CDynamicStringAccessorW  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md)|检索列信息。|  
|[GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)|按行检索表的整个内容。|  
  
## 备注  
 但是，`CXMLAccessor` 与 `CDynamicStringAccessorW` 的区别在于它从数据存储访问的所有数据都转换为 XML 格式的 \(即带标记的\) 数据。  对于输出特别有用。XML 支持网页。  XML 标记名会尽可能密切地符合数据存储区的列名。  
  
 使用 `CDynamicAccessor` 方法获取列信息。  使用该列信息在运行时动态创建访问器。  
  
 该列信息存储在由此类创建并管理的缓冲区中。  使用 [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)，获取列信息。[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) 或按行获取列数据。  
  
## 示例  
 [!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/CPP/cxmlaccessor-class_1.cpp)]  
  
## 要求  
 **标题**:atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 类](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CDynamicStringAccessor 类](../../data/oledb/cdynamicstringaccessor-class.md)   
 [CDynamicStringAccessorA 类](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW 类](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)