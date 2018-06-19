---
title: db_table |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_table
dev_langs:
- C++
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f482e93f124d73d48d1de66f3feb1779146025d0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874338"
---
# <a name="dbtable"></a>db_table
将打开一个 OLE DB 表。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ db_table(   
   db_table,   
   name,   
   source_name,   
   hresult   
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *db_table*  
 指定数据库表 （例如"Products") 的名称的字符串。  
  
  名称（可选）  
 用于处理与表的句柄的名称。 如果你想要返回的结果的多个行，必须指定此参数。 **db_table**生成指定的变量*名称*可用来遍历行集或执行操作的多个查询。  
  
  source_name（可选）  
 将 `CSession` 特性应用到其（在其上运行命令）的类的 `db_source` 变量或实例。 请参阅 [db_source](../windows/db-source.md)。  
  
 `hresult` （可选）  
 标识将接收此数据库命令的 `HRESULT` 的变量。 如果该变量不存在，属性将自动插入。  
  
## <a name="remarks"></a>备注  
 **db_table**创建[CTable](../data/oledb/ctable-class.md)对象，该 OLE DB 使用者用来打开表对象。 你可以使用此属性仅在类级别;不能使用它内联。 使用**db_column**将表中的列绑定到变量; 使用**db_param**来分隔 （设置的参数类型，因此上） 的参数。  
  
 当使用者特性提供程序应用于类时此属性时，编译器将该类重命名为\_*类名*访问器，其中*类名*是你为指定的名称类，并且编译器还将创建一个名为类*类名*，它派生自\_*类名*访问器。  将在类视图中看到这两个类。  
  
## <a name="example"></a>示例  
 下面的示例打开以供产品表`CProducts`。  
  
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
  
 应用程序中使用此属性的示例，请参阅示例[AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409)和[MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e)。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**class**， `struct`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者特性](../windows/ole-db-consumer-attributes.md)   
