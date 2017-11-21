---
title: "db_source |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.db_source
dev_langs: C++
helpviewer_keywords: db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 89f07745d2a9f0f832f42c512e0671b4114a80c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="dbsource"></a>db_source
创建与数据源的连接。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ db_source(   
   db_source,   
   name,   
   hresult   
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *db_source*  
 用于连接到数据源的连接字符串。 有关连接字符串的格式，请参阅[连接字符串和数据链接](https://msdn.microsoft.com/en-us/library/ms718376.aspx)在 Microsoft 数据访问组件 (MDAC) SDK。  
  
  名称（可选）  
 当你使用`db_source`类、*名称*是具有的数据源对象的一个实例`db_source`特性应用于它 （请参阅示例 1）。 当你使用`db_source`在方法实现中，内联*名称*是一个变量 （本地到方法），可用来访问数据源 （请参见示例 2）。 请将此传递*名称*到`source_name`参数**db_command**要与命令关联的数据源。  
  
 `hresult`（可选）  
 标识将接收此数据库命令的 `HRESULT` 的变量。 如果该变量不存在，属性将自动插入。  
  
## <a name="remarks"></a>备注  
 `db_source`创建[CDataSource](../data/oledb/cdatasource-class.md)和[CSession](../data/oledb/csession-class.md)对象，一起表示与 OLE DB 使用者数据源的连接。  
  
 当你使用`db_source`类、`CSession`对象成为类的成员。  
  
 当你使用`db_source`在方法范围内，将在方法中，执行插入的代码和`CSession`对象被创建为本地变量。  
  
 `db_source`与类或方法中，将添加数据源属性。 结合使用**db_command** (此方法采用`db_source`*名称*参数作为其`source_name`参数)。  
  
 当使用者特性提供程序应用于类时此属性时，编译器将该类重命名为\_*类名*访问器，其中*类名*是你为指定的名称类，并且编译器还将创建一个名为类*类名*，它派生自\_*类名*访问器。  将在类视图中看到这两个类。  
  
 应用程序中使用此属性的示例，请参阅示例[AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409)和[MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e)。  
  
## <a name="example"></a>示例  
 此示例调用`db_source`置于类上以创建与数据源的连接`ds`使用 Northwind 数据库。 `ds`是数据源，可以使用用于内部的句柄`CMyCommand`类。  
  
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
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**、 `struct`、成员、方法、本地|  
|**可重复**|No|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另请参阅  
 [OLE DB 使用者特性](../windows/ole-db-consumer-attributes.md)   
