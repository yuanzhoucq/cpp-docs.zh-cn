---
title: "db_param |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.db_param
dev_langs:
- C++
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5224c406f6e10cd4ef9f0ed64fbdbd7c5cc8e62
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dbparam"></a>db_param
将指定的成员变量与一个输入或输出参数相关联，并分隔变量。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `ordinal`  
 列号 (**DBCOLUMNINFO**序号) 要将数据绑定到行集中的字段相对应。  
  
 *paramtype* （可选）  
 要为参数设置的类型。 提供程序仅支持参数 I/O 类型所支持的基础数据源。 类型是一个或多个组合**DBPARAMIOENUM**值：  
  
-   **DBPARAMIO_INPUT** 输入参数。  
  
-   **DBPARAMIO_OUTPUT** 输出参数。  
  
-   **DBPARAMIO_NOTPARAM** 访问器没有参数。 设置**eParamIO**到行中的此值访问器可提醒用户将忽略参数。  
  
 *dbtype* （可选）  
 OLE DB[类型指示符](https://msdn.microsoft.com/en-us/library/ms711251.aspx)列条目。  
  
 *精度*（可选）  
 要用于列条目精度。 有关详细信息，请参阅说明**bPrecision**元素[DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *缩放*（可选）  
 要使用的列项的比例。 有关详细信息，请参阅说明**bScale**元素[DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *状态*（可选）  
 成员变量，用来保存此列的状态。 状态指示该列的值是数据值或某些其他值，如**NULL**。 有关可能的值，请参阅[状态](https://msdn.microsoft.com/en-us/library/ms722617.aspx)中*OLE DB 程序员参考*。  
  
 *长度*（可选）  
 成员变量，用来保存列的大小，以字节为单位。  
  
## <a name="remarks"></a>备注  
 **db_param**定义参数，在命令中使用; 因此将它与**db_command**。 例如，你可以使用**db_param**若要将 SQL 查询或存储的过程中的参数绑定。 由问号 （？），表示在存储过程的参数，你应绑定参数的顺序中的数据成员。  
  
 **db_param**分隔可以参与 OLE DB 的成员数据`ICommandWithParameters`-基于绑定。 它将设置参数类型 （输入或输出）、 OLE DB 类型、 精度、 小数位数、 状态和为指定的参数的长度。 此属性将插入的 OLE DB 使用者宏 BEGIN_PARAM_MAP...END_PARAM_MAP。 以将标记每个成员**db_param**属性中的映射中的 COLUMN_ENTRY 窗体占用一个条目。  
  
 **db_param**与请结合使用[db_table](../windows/db-table.md)或[db_command](../windows/db-command.md)属性。  
  
 当使用者特性提供程序应用于类时此属性时，编译器将该类重命名为\_*类名*访问器，其中*类名*是你为指定的名称类，并且编译器还将创建一个名为类*类名*，它派生自\_*类名*访问器。  将在类视图中看到这两个类。  
  
## <a name="example"></a>示例  
 下面的示例创建了基于 Northwind 数据库中的 SalesbyYear 存储过程的命令类。 它是相关联的存储过程中的第一个参数`m_RETURN_VALUE`变量，并将其定义为输出参数。 它是相关联的最后两个 （输入） 参数与`m_Beginning_Date`和`m_Ending_Date`。  
  
 下面的示例将`nOutput`变量使用输出参数。  
  
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
  
## <a name="requirements"></a>惠?  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**、 `struct`、成员、方法、本地|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者特性](../windows/ole-db-consumer-attributes.md)   
