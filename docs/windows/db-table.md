---
title: "db_table | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.db_table"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_table attribute"
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# db_table
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

打开 OLE DB 表。  
  
## 语法  
  
```  
  
      [ db_table(   
   db_table,   
   name,   
   source_name,   
   hresult   
) ]  
```  
  
#### 参数  
 *db\_table*  
 指定数据库表的名称字符串 \(如 “产品”\)。  
  
 *名称* \(可选\)  
 使用与表使用处理的名称。  ，如果要返回多个结果，一行必须指定此参数。  **db\_table** 生成与可用于遍历行集合或执行多个操作查询的指定名称的变量。  
  
 *source\_name* \(可选\)  
 具有 `db_source` 特性类的 `CSession` 变量或实例应用于它在哪些命令执行。  [db\_source](../windows/db-source.md)参见。  
  
 `hresult`（可选）  
 标识要接收此数据库命令 `HRESULT` 的变量。  如果变量不存在，则将属性自动插入。  
  
## 备注  
 **db\_table** 创建一 [CTable](../data/oledb/ctable-class.md) 对象， OLE DB 使用者用于打开表。  只能使用该属性在类级别;您不能使用它内联。  使用 **db\_column** 表绑定列给变量;使用 **db\_param** 分隔 \(将参数类型等\) 参数。  
  
 当使用者属性提供程序应用此特性应用于类，编译器将类重命名为 \_TheClassNameAccessor， *TheClassName* 的名称就是您为该类，因此，编译器还将创建一个名为 *TheClassName 的* 类 *，* 从 \_TheClassNameAccessor 派生。  在类视图中，您将看到两类。  
  
## 示例  
 下面的示例打开 products 表 `CProducts`供使用。  
  
```  
// db_table.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_table(L"dbo.Products") ]  
class CProducts {  
   [ db_column("1") ] LONG m_ProductID;  
};  
```  
  
 有关用于应用程序的此属性的示例，请参见示例 [AtlAgent](http://msdn.microsoft.com/zh-cn/52bef5da-c1a0-4223-b4e6-9e464b6db409) 和 [MultiRead](http://msdn.microsoft.com/zh-cn/5a2a915a-77dc-492f-94b2-1b809995dd5e)。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [OLE DB Consumer Attributes](../windows/ole-db-consumer-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)