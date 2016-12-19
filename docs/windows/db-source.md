---
title: "db_source | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.db_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_source attribute"
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# db_source
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建与数据源的连接。  
  
## 语法  
  
```  
  
      [ db_source(   
   db_source,   
   name,   
   hresult   
) ]  
```  
  
#### 参数  
 *db\_source*  
 使用的连接字符串连接到数据源。  有关连接字符串的格式，请参见 Microsoft 数据访问组件 \(mdac\) SDK 的 [连接字符串和数据链接](https://msdn.microsoft.com/en-us/library/ms718376.aspx) \(MDAC\)。  
  
 *名称* \(可选\)  
 当使用类上的 `db_source` ， *名称* 是具有 `db_source` 特性应用于数据源对象的实例 \(请参见示例 1\)。  在实现方法时使用 `db_source` 内联， *名称* 是可用于访问数据源的变量 \(对方法的局部\) \(请参见示例 2\)。  通过此 *名称* 来 **db\_command** 的 `source_name` 参数关联数据源与命令。  
  
 `hresult`（可选）  
 标识要接收此数据库命令 `HRESULT` 的变量。  如果变量不存在，则将属性自动插入。  
  
## 备注  
 `db_source` 创建 [CDataSource](../data/oledb/cdatasource-class.md) 和一 [CSession](../data/oledb/csession-class.md) 对象，一起表示与 OLE DB 使用者数据源的连接。  
  
 当使用类上的 `db_source` ， `CSession` 对象都会成为类的成员。  
  
 当您在方法使用 `db_source` ，插入的代码在方法范围内，都将执行，并 `CSession` 对象创建为局部变量。  
  
 `db_source` 添加数据源属性为类或方法内。  它使用 \(结合使用采用 `db_source` *名称* 参数作为其 `source_name` 参数\) 的 **db\_command** 。  
  
 当使用者属性提供程序应用此特性应用于类，编译器将类重命名为 \_TheClassNameAccessor， *TheClassName* 的名称就是您为该类，因此，编译器还将创建一个名为 *TheClassName 的* 类 *，* 从 \_TheClassNameAccessor 派生。  在类视图中，您将看到两类。  
  
 有关用于应用程序的此属性的示例，请参见示例 [AtlAgent](http://msdn.microsoft.com/zh-cn/52bef5da-c1a0-4223-b4e6-9e464b6db409) 和 [MultiRead](http://msdn.microsoft.com/zh-cn/5a2a915a-77dc-492f-94b2-1b809995dd5e)。  
  
## 示例  
 使用 Northwind 数据库，此示例调用类的 `db_source` 创建与数据源 `ds` 的连接。  `ds` 是数据源的句柄，可以在内部用于 `CMyCommand` 类。  
  
```  
// db_source_1.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[  
  db_source(L"my_connection_string", name="ds"),  
  db_command(L"select * from Products")  
]  
class CMyCommand {};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`，成员，方法，本地|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [OLE DB Consumer Attributes](../windows/ole-db-consumer-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)