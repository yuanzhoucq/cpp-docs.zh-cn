---
title: "CDynamicAccessor 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CDynamicAccessor"
  - "ATL::CDynamicAccessor"
  - "CDynamicAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicAccessor 类"
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CDynamicAccessor 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使您可以在不知道数据库架构（数据库的基础结构）的情况下访问数据源。  
  
## 语法  
  
```  
class CDynamicAccessor : public CAccessorBase  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cdynamicaccessor-addbindentry.md)|当重写默认访问器时，添加输入绑定到输出列。|  
|[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)|实例化和初始化 `CDynamicAccessor` 对象。|  
|[关闭](../../data/oledb/cdynamicaccessor-close.md)|断开所有列，释放分配的内存，然后释放类中[IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx)的接口指针。|  
|[GetBookmark](../../data/oledb/cdynamicaccessor-getbookmark.md)|检索当前行的书签。|  
|[GetBlobHandling](../../data/oledb/cdynamicaccessor-getblobhandling.md)|检索当前行处理 BLOB 的值。|  
|[GetBlobSizeLimit](../../data/oledb/cdynamicaccessor-getblobsizelimit.md)|检索以字节为单位的最大BLOB大小。|  
|[GetColumnCount](../../data/oledb/cdynamicaccessor-getcolumncount.md)|检索中列数的行集合。|  
|[GetColumnFlags](../../data/oledb/cdynamicaccessor-getcolumnflags.md)|检索列特性。|  
|[GetColumnInfo](../../data/oledb/cdynamicaccessor-getcolumninfo.md)|检索列元数据。|  
|[GetColumnName](../../data/oledb/cdynamicaccessor-getcolumnname.md)|检索指定的列的名称。|  
|[GetColumnType](../../data/oledb/cdynamicaccessor-getcolumntype.md)|检索指定列的数据类型。|  
|[GetLength](../../data/oledb/cdynamicaccessor-getlength.md)|检索列中值的最大可能长度以字节为长度。|  
|[GetOrdinal](../../data/oledb/cdynamicaccessor-getordinal.md)|检索给定列名的索引。|  
|[GetStatus](../../data/oledb/cdynamicaccessor-getstatus.md)|检索指定列的状态。|  
|[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)|从缓冲区检索数据。|  
|[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)|设置当前行处理 BLOB 的值。|  
|[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)|以字节为单位的最大BLOB大小。|  
|[SetLength](../../data/oledb/cdynamicaccessor-setlength.md)|设置数据列的长度（以字节为单位）。|  
|[SetStatus](../../data/oledb/cdynamicaccessor-setstatus.md)|设置指定列的状态。|  
|[SetValue](../../data/oledb/cdynamicaccessor-setvalue.md)|数据存储到缓冲区。|  
  
## 备注  
 利用`CDynamicAccessor` 方法获取列信息，如列名、列数和数据类型等等。  然后使用该列信息在运行时动态创建访问器。  
  
 列信息存储在由该类创建并管理的缓冲区中。  使用 [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md) 从该缓冲区中获取数据。  
  
 讨论并使用有关实例的动态访问器类，请参见 [使用动态访问器](../../data/oledb/using-dynamic-accessors.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 类](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)