---
title: db_table |Microsoft Docs
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
ms.openlocfilehash: 91eea8bd751e4e8e843fb2d052f2b4a71f9bdc38
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570332"
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
 指定 （例如"产品"） 的数据库表的名称的字符串。  
  
  名称（可选）  
 句柄用于处理表的名称。 如果你想要返回多个行的结果，必须指定此参数。 **db_table**生成具有指定的变量*名称*可用来遍历行集或执行多个操作查询。  
  
  source_name（可选）  
 将 `CSession` 特性应用到其（在其上运行命令）的类的 `db_source` 变量或实例。 请参阅 [db_source](../windows/db-source.md)。  
  
 *hresult* （可选）  
 标识将接收此数据库命令的 HRESULT 的变量。 如果该变量不存在，属性将自动插入。  
  
## <a name="remarks"></a>备注  
 **db_table**创建[CTable](../data/oledb/ctable-class.md)对象，OLE DB 使用者用于打开表。 只能在类级别，则使用此属性它不能使用内联。 使用`db_column`若要将表中的列绑定到变量; 使用`db_param`来分隔 （该参数的类型，因此在上设置） 的参数。  
  
 编译器时使用者特性提供程序适用于类，此属性，将重命名为类\_ *YourClassName*访问器，其中*名为 YourClassName*是您为指定的名称类和编译器还将创建一个名为类*名为 YourClassName*，它派生\_*名为 YourClassName*访问器。  将在类视图中看到这两个类。  
  
## <a name="example"></a>示例  
 下面的示例打开 Products 表以供`CProducts`。  
  
```cpp  
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
  
 有关在应用程序中使用此属性的一个示例，请参阅示例[AtlAgent](http://msdn.microsoft.com/52bef5da-c1a0-4223-b4e6-9e464b6db409)并[MultiRead](http://msdn.microsoft.com/5a2a915a-77dc-492f-94b2-1b809995dd5e)。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**，**结构**|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者特性](../windows/ole-db-consumer-attributes.md)   