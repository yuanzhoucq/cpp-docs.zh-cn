---
title: "CDynamicParameterAccessor 类 | Microsoft Docs"
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
  - "ATL.CDynamicParameterAccessor"
  - "ATL::CDynamicParameterAccessor"
  - "CDynamicParameterAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicParameterAccessor 类"
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicParameterAccessor 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

类似于 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)，但通过调用 [ICommandWithParameters](https://msdn.microsoft.com/en-us/library/ms712937.aspx) 接口获取要调用的参数信息。  
  
## 语法  
  
```  
class CDynamicParameterAccessor : public CDynamicAccessor  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-cdynamicparameteraccessor.md)|构造函数。|  
|[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)|从缓冲区中检索参数数据。|  
|[GetParamCount](../../data/oledb/cdynamicparameteraccessor-getparamcount.md)|检索访问器中的参数数目。|  
|[GetParamIO](../../data/oledb/cdynamicparameteraccessor-getparamio.md)|确定指定参数是输入参数还是输出参数。|  
|[GetParamLength](../../data/oledb/cdynamicparameteraccessor-getparamlength.md)|检索存储在缓冲区中的指定参数的长度。|  
|[GetParamName](../../data/oledb/cdynamicparameteraccessor-getparamname.md)|检索指定参数的名称。|  
|[GetParamStatus](../../data/oledb/cdynamicparameteraccessor-getparamstatus.md)|检索存储在缓冲区中的指定参数的状态。|  
|[GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md)|检索存储在缓冲区中的指定参数的字符串数据。|  
|[GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)|检索指定参数的数据类型。|  
|[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)|使用参数数据设置缓冲区。|  
|[SetParamLength](../../data/oledb/cdynamicparameteraccessor-setparamlength.md)|设置存储在缓冲区中的指定参数的长度。|  
|[SetParamStatus](../../data/oledb/cdynamicparameteraccessor-setparamstatus.md)|设置存储在缓冲区中的指定参数的状态。|  
|[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)|设置存储在缓冲区中的指定参数的字符串数据。|  
  
## 备注  
 访问接口必须支持 `ICommandWithParameters` 以便使用者使用此类。  
  
 参数信息存储在由此类创建和管理的缓冲区中。 通过使用 [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) 和 [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md) 从缓冲区中获取参数数据。  
  
 有关演示如何使用此类执行 SQL Server 存储过程并获取输出参数值的示例，请参阅知识库文章 Q058860“如何：使用 CDynamicParameterAccessor 执行存储过程”。 知识库文章位于 MSDN 库的 Visual Studio 文档或 [http:\/\/support.microsoft.com\/](http://support.microsoft.com) 中。  
  
## 要求  
 **标头**：atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 类](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)