---
title: "db_accessor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.db_accessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_accessor attribute"
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# db_accessor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

分组联接 `IAccessor`基于绑定的 **db\_column** 属性。  
  
## 语法  
  
```  
  
      [ db_accessor(   
   num,   
   auto   
) ]  
```  
  
#### 参数  
 *num*  
 指定访问器编号 \(从零开始的整数索引\)。  使用整数或已定义的值，则必须以递增的顺序指定访问器编号，。  
  
 *自动*  
 指定的布尔值是否访问器自动检索 \(**TRUE**\) 不会检索 \(**错误**\)。  
  
## 备注  
 **db\_accessor** 定义后续 **db\_column** 的基础 OLE DB 访问器和在同一个类或函数中的 **db\_param** 属性。  **db\_accessor** 中可用的成员级别和用于分组联接 OLE DB `IAccessor`基于绑定的 **db\_column** 属性。  它与 **db\_table** 或 **db\_command** 特性一起使用。  调用此属性与调用 [BEGIN\_ACCESSOR](../data/oledb/begin-accessor.md) 和 [END\_ACCESSOR](../data/oledb/end-accessor.md) 宏。  
  
 **db\_accessor** 生成一个行集合并将其绑定到相应的访问器映射。  如果不调用 **db\_accessor**，访问器 0 将自动生成，因此，所有列绑定将映射到此访问器块。  
  
 **db\_accessor** 组数据库列绑定到一个或多个访问器中。  有关需要使用多个访问器的方案的讨论，请参见 [行集合上使用多个访问器](../data/oledb/using-multiple-accessors-on-a-rowset.md)。  请参见 “用户记录为多个访问器支持” [用户记录](../data/oledb/user-records.md)的。  
  
 当使用者属性提供程序应用此特性应用于类，编译器将类重命名为 \_TheClassNameAccessor， *TheClassName* 的名称就是您为该类，因此，编译器还将创建一个名为 *TheClassName 的* 类 *，* 从 \_TheClassNameAccessor 派生。  在类视图中，您将看到两类。  
  
## 示例  
 下面的示例使用 **db\_accessor** 分组列在 Northwind 数据库的 orders 表中到两个访问器。  访问器 0 是自动访问器，因此，访问器 1 不是。  
  
```  
// cpp_attr_ref_db_accessor.cpp  
// compile with: /LD /link /OPT:NOREF  
#define _ATL_ATTRIBUTES  
#include <atlbase.h>  
#include <atldbcli.h>  
  
[ db_command(L"SELECT LastName, FirstName FROM Orders") ]  
class CEmployees {  
public:  
   [ db_accessor(0, TRUE) ];  
   [ db_column("1") ] LONG m_OrderID;  
   [ db_column("2") ] TCHAR m_CustomerID[6];  
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;   
  
   [ db_accessor(1, FALSE) ];  
   [ db_column("8") ] CURRENCY m_Freight;  
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|特性块|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [OLE DB Consumer Attributes](../windows/ole-db-consumer-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)