---
title: "db_column | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.db_column"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_column attribute"
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# db_column
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将指定的列设置为行集合中的变量。  
  
## 语法  
  
```  
  
      [ db_column(   
   ordinal,   
   dbtype,   
   precision,   
   scale,   
   status,   
   length   
) ]  
```  
  
#### 参数  
 `ordinal`  
 序号列数 \(**DBCOLUMNINFO** 序号\) 或列名 \(ANSI 或 Unicode 字符串\) 与绑定数据的行集合的字段相对应。  如果使用数字，则可以跳过连续的序号 \(例如:1， 2， 3， 5\)。  该名称可能包含空格，如果您使用的 OLE DB 提供程序支持它。  例如，可以使用以下格式之一:  
  
```  
[db_column("2")] TCHAR szCity[30];  
[db_column(L"city_name")] TCHAR szCity[30];  
```  
  
 *dbtype* \(可选\)  
 列项的 OLE DB [键入指示器](https://msdn.microsoft.com/en-us/library/ms711251.aspx) 。  
  
 *精度* \(可选\)  
 为列项将使用的精度。  有关详细信息，请参见 [DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)的 `bPrecision` 元素的说明  
  
 *缩放* \(可选\)  
 为列项将使用缩放。  有关详细信息，请参见 [DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)的 `bScale` 元素的说明  
  
 *状态* \(可选\)  
 用于的成员变量保存该列的状态。  状态指示列值是否为数据绑定值或其他值，如 **NULL**。  有关可能的值，请参见 " *OLE DB 程序员的*[状态](https://msdn.microsoft.com/en-us/library/ms722617.aspx)*引用*。  
  
 *长度* \(可选\)  
 用于的成员变量来保存列的大小 \(以字节为单位\)。  
  
## 备注  
 **db\_column** 绑定指定的表列到行集合中的变量。  它分隔可参与 OLE DB `IAccessor`基于绑定的数据成员。  此特性设置了使用 OLE DB 使用者宏通常定义的列映射 [BEGIN\_COLUMN\_MAP](../data/oledb/begin-column-map.md)、 [END\_COLUMN\_MAP](../data/oledb/end-column-map.md)和 [COLUMN\_ENTRY](../data/oledb/column-entry.md)。  这些操作 OLE DB [DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx) 绑定指定列。  在标有 **db\_column** 属性以列项的窗体中，的每个成员将占用在列映射的项。  因此，您调用您在命令或表类会将列映射，也就是说，将此属性。  
  
 与 [db\_table](../windows/db-table.md) 或 [db\_command](../windows/db-command.md) 特性一起使用 **db\_column** 。  
  
 当使用者属性提供程序应用此特性应用于类，编译器将类重命名为 \_TheClassNameAccessor， *TheClassName* 的名称就是您为该类，因此，编译器还将创建一个名为 *TheClassName 的* 类 *，* 从 \_TheClassNameAccessor 派生。  在类视图中，您将看到两类。  
  
 在应用程序中使用的此属性的示例，请参见示例 [AtlAgent](http://msdn.microsoft.com/zh-cn/52bef5da-c1a0-4223-b4e6-9e464b6db409)和 [MultiRead](http://msdn.microsoft.com/zh-cn/5a2a915a-77dc-492f-94b2-1b809995dd5e)。  
  
## 示例  
 此示例在表中将列绑定到 **long** 数据成员并指定状态和长度字段。  
  
```  
// db_column_1.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_command(L"Select * from Products") ]  
class CProducts {  
   DBSTATUS m_dwProductIDStatus;  
   DBLENGTH m_dwProductIDLength;  
  
   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;  
};  
```  
  
## 示例  
 此示例将四列设置为 **long**、字符串、一个时间戳和一个 **DB\_NUMERIC** 整数，按此顺序。  
  
```  
// db_column_2.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_command(L"Select * from Products") ]  
class CProducts {  
   [db_column("1")] LONG m_OrderID;  
   [db_column("2")] TCHAR m_CustomerID[6];  
   [db_column("4")] DB_NUMERIC m_OrderDate;     
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;  
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`，成员，方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [OLE DB Consumer Attributes](../windows/ole-db-consumer-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)