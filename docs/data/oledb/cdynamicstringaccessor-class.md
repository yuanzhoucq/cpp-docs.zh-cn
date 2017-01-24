---
title: "CDynamicStringAccessor 类 | Microsoft Docs"
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
  - "CDynamicStringAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicStringAccessor 类"
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicStringAccessor 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使您可以在不知道数据库架构（数据库的基础结构）的情况下访问数据源。  
  
## 语法  
  
```  
  
      template< typename BaseType, DBTYPEENUM OleDbType >  
class CDynamicStringAccessorT : public CDynamicAccessor  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)|恢复检索指定列数据为字符串。|  
|[设置字符串](../../data/oledb/cdynamicstringaccessor-setstring.md)|设置指定列数据为字符串。|  
  
## 备注  
 [](../../data/oledb/cdynamicaccessor-class.md "CDynamicAccessor Class")  `请求数据以由提供程序报告的本机格式，而 CDynamicStringAccessor` 则请求提供程序以字符串数据形式获取在数据存储区中存取的所有数据。  这对于不需要计算数据存储区中的值的简单任务（如显示或打印数据存储区的内容）很有用。  
  
 数据存储区中数据的本机类型并不重要；只要提供程序支持数据转换，它会提供有关字符串格式的数据。  如果提供程序不支持从本机数据类型转换为字符串（不是公共的\)，请求的调用将返回 **DB\_S\_ERRORSOCCURED**成功值，并且，相应列的状态将指示 **DBSTATUS\_E\_CANTCONVERTVALUE**的转换问题。  
  
 使用 `CDynamicStringAccessor` 方法获取列信息。  使用该列信息在运行时动态创建访问器。  
  
 该列信息存储在由此类创建并管理的缓冲区中。  使用 [CDynamicStringAccessor::GetString](../../data/oledb/cdynamicstringaccessor-getstring.md) 从此缓冲区中获取数据，或使用 [CDynamicStringAccessor::SetString](../../data/oledb/cdynamicstringaccessor-setstring.md) 将数据存储到此缓冲区中。  
  
 讨论并使用有关实例的动态访问器类，请参见 [使用动态访问器](../../data/oledb/using-dynamic-accessors.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 类](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessorA 类](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW 类](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CXMLAccessor 类](../../data/oledb/cxmlaccessor-class.md)