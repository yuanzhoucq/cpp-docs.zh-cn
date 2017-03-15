---
title: "db_param | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.db_param"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_param attribute"
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# db_param
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将指定的成员变量与输入或输出参数并将变量。  
  
## 语法  
  
```  
  
      [ db_param(   
   ordinal,   
   paramtype="DBPARAMIO_INPUT",   
   dbtype,   
   precision,   
   scale,   
   status,   
   length  
) ]  
```  
  
#### 参数  
 `ordinal`  
 列数 \(**DBCOLUMNINFO** 序号\) 与绑定数据的行集合的字段相对应。  
  
 *paramtype* \(可选\)  
 设置类型为参数。  提供程序支持参数由基础数据源支持的 I\/O 类型。  该类型是一个或多 **DBPARAMIOENUM** 值的组合:  
  
-   **DBPARAMIO\_INPUT**输入参数。  
  
-   **DBPARAMIO\_OUTPUT**输出参数。  
  
-   **DBPARAMIO\_NOTPARAM** 访问器没有参数。  将设置为值的 **eParamIO** 在行访问器提醒用户参数将被忽略。  
  
 *dbtype* \(可选\)  
 列项的 OLE DB [键入指示器](https://msdn.microsoft.com/en-us/library/ms711251.aspx) 。  
  
 *精度* \(可选\)  
 为列项将使用的精度。  有关详细信息，请参见 [DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)的 **bPrecision** 元素的说明  
  
 *缩放* \(可选\)  
 为列项将使用缩放。  有关详细信息，请参见 [DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)的 **bScale** 元素的说明  
  
 *状态* \(可选\)  
 用于的成员变量保存该列的状态。  状态指示列值是否为数据绑定值或其他值，如 **NULL**。  有关可能的值，请参见 " *OLE DB 程序员的*[状态](https://msdn.microsoft.com/en-us/library/ms722617.aspx)*引用*。  
  
 *长度* \(可选\)  
 用于的成员变量来保存列的大小 \(以字节为单位\)。  
  
## 备注  
 **db\_param** 定义可在命令的参数;因此将它与 **db\_command**。  例如，可以使用 **db\_param** 为固定参数在 SQL 查询或存储过程。  在存储过程中的参数表示由问号 \(?\)，因此，您应绑定数据成员按参数的出现顺序。  
  
 **db\_param** 分隔可参与 OLE DB `ICommandWithParameters`基于绑定的数据成员。  它将参数类型 \(输入或输出\)， OLE DB 类型、精度、缩放、状态和长度为指定的参数。  此特性插入 OLE DB 使用者宏 BEGIN\_PARAM\_MAP…  END\_PARAM\_MAP.  在标有 **db\_param** 属性以 COLUMN\_ENTRY 形式，的每个成员将占用在映射的项。  
  
 **db\_param** 与 [db\_table](../windows/db-table.md) 或 [db\_command](../windows/db-command.md) 特性一起使用。  
  
 当使用者属性提供程序应用此特性应用于类，编译器将类重命名为 \_TheClassNameAccessor， *TheClassName* 的名称就是您为该类，因此，编译器还将创建一个名为 *TheClassName 的* 类 *，* 从 \_TheClassNameAccessor 派生。  在类视图中，您将看到两类。  
  
## 示例  
 下面的示例 Northwind 数据库中创建基于 SalesbyYear 存储过程的命令类。  其关联在存储过程中的第一个参数与 `m_RETURN_VALUE` 变量，并定义为输出参数。  其关联最后两个输入参数 \(\) 与 `m_Beginning_Date` 和 `m_Ending_Date`。  
  
 下面的示例关联 `nOutput` 变量与输出参数。  
  
```  
// db_param.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_source(L"my_connection_string"),   
  db_command(L"{ ? = CALL dbo.\"Sales by Year\"(?,?) }")   
]  
struct CSalesbyYear {  
   DBSTATUS m_dwShippedDateStatus;  
   DBSTATUS m_dwOrderIDStatus;  
   DBSTATUS m_dwSubtotalStatus;  
   DBSTATUS m_dwYearStatus;  
  
   DBLENGTH m_dwShippedDateLength;  
   DBLENGTH m_dwOrderIDLength;  
   DBLENGTH m_dwSubtotalLength;  
   DBLENGTH m_dwYearLength;  
  
   // Bind columns  
   [ db_column("1", status="m_dwShippedDateStatus", length="m_dwShippedDateLength") ] DBTIMESTAMP m_ShippedDate;  
   [ db_column("2", status="m_dwOrderIDStatus", length="m_dwOrderIDLength") ] LONG m_OrderID;  
   [ db_column("3", status="m_dwSubtotalStatus", length="m_dwSubtotalLength") ] CURRENCY m_Subtotal;  
   [ db_column("4", status="m_dwYearStatus", length="m_dwYearLength") ] TCHAR m_Year[31];  
  
   // Bind parameters  
   [ db_param("1", paramtype="DBPARAMIO_OUTPUT") ] LONG m_RETURN_VALUE;  
   [ db_param("2", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Beginning_Date;  
   [ db_param("3", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Ending_Date;  
};  
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