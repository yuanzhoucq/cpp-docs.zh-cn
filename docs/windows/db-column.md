---
title: "db_column |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.db_column
dev_langs: C++
helpviewer_keywords: db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8fda1cfd5b23ae94da6be070e59add2854fb2687
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="dbcolumn"></a>db_column
将指定的列绑定到在行集中的变量。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `ordinal`  
 序号列号 (**DBCOLUMNINFO**序号) 或要将数据绑定到行集中的字段相对应的列名称 （ANSI 或 Unicode 字符串）。 如果使用数字，则可以跳过连续序号 (例如： 1、 2、 3、 5)。 名称可以包含空格，如果你使用的 OLE DB 访问接口支持它。 例如，可以使用以下格式：  
  
```  
[db_column("2")] TCHAR szCity[30];  
[db_column(L"city_name")] TCHAR szCity[30];  
```  
  
 *dbtype* （可选）  
 OLE DB[类型指示符](https://msdn.microsoft.com/en-us/library/ms711251.aspx)列条目。  
  
 *精度*（可选）  
 要用于列条目精度。 有关详细信息，请参阅说明`bPrecision`元素[DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *缩放*（可选）  
 要使用的列项的比例。 有关详细信息，请参阅说明`bScale`元素[DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *状态*（可选）  
 成员变量，用来保存此列的状态。 状态指示该列的值是数据值或某些其他值，如**NULL**。 有关可能的值，请参阅[状态](https://msdn.microsoft.com/en-us/library/ms722617.aspx)中*OLE DB 程序员参考*。  
  
 *长度*（可选）  
 成员变量，用来保存列的大小，以字节为单位。  
  
## <a name="remarks"></a>备注  
 **db_column**将指定的表列绑定到在行集中的变量。 它分隔可以参与 OLE DB 的成员数据`IAccessor`-基于绑定。 此属性将设置通常使用 OLE DB 使用者宏定义列映射[BEGIN_COLUMN_MAP](../data/oledb/begin-column-map.md)， [END_COLUMN_MAP](../data/oledb/end-column-map.md)，和[COLUMN_ENTRY](../data/oledb/column-entry.md)。 这些操作 OLE DB [DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)可将指定的列绑定。 以将标记每个成员**db_column**属性中的列映射中的列项的窗体占用一个条目。 因此，你调用此属性将放置列映射，即，命令或表类中。  
  
 使用**db_column**结合使用[db_table](../windows/db-table.md)或[db_command](../windows/db-command.md)属性。  
  
 当使用者特性提供程序应用于类时此属性时，编译器将该类重命名为\_*类名*访问器，其中*类名*是你为指定的名称类，并且编译器还将创建一个名为类*类名*，它派生自\_*类名*访问器。  将在类视图中看到这两个类。  
  
 有关应用程序中使用此属性的示例，请参阅示例[AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409)，和[MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e)。  
  
## <a name="example"></a>示例  
 此示例将列绑定到表中**长**数据成员，并指定状态和长度字段。  
  
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
  
## <a name="example"></a>示例  
 此示例将绑定到的四个列**长**，字符字符串、 一个时间戳，和一个**DB_NUMERIC**整数，该顺序。  
  
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
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`，成员，则方法|  
|**可重复**|No|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另请参阅  
 [OLE DB 使用者特性](../windows/ole-db-consumer-attributes.md)   
 [类特性](../windows/class-attributes.md)   
