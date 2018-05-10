---
title: db_accessor |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_accessor
dev_langs:
- C++
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b81e55500a8ff44c887bed592c9472c5a8d3ea1d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="dbaccessor"></a>db_accessor
组**db_column**参与特性`IAccessor`-基于绑定。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ db_accessor(   
   num,   
   auto   
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *num*  
 指定访问器数目 （从零开始的整数索引）。 你必须指定访问器中增加的数字顺序，使用整数或定义的值。  
  
 *auto*  
 一个布尔值，指定是否自动检索访问器 (**TRUE**) 未检索到或 (**FALSE**)。  
  
## <a name="remarks"></a>备注  
 **db_accessor**定义为基础的 OLE DB 取值函数后续**db_column**和**db_param**相同类或函数中的属性。 **db_accessor**在成员级别为可用，并且使用到组**db_column**参与 OLE DB 的特性`IAccessor`-基于绑定。 请结合使用**db_table**或**db_command**属性。 调用此属性是类似于调用[BEGIN_ACCESSOR](../data/oledb/begin-accessor.md)和[END_ACCESSOR](../data/oledb/end-accessor.md)宏。  
  
 **db_accessor**生成行集，并将其绑定到相应的访问器映射。 如果不调用**db_accessor**，则将自动生成访问器 0，而所有列绑定将都映射到此访问器块。  
  
 **db_accessor**组数据库列绑定到一个或多个访问器。 你需要使用多个访问器的方案的讨论，请参阅[行集上使用多个访问器](../data/oledb/using-multiple-accessors-on-a-rowset.md)。 另请参阅"用户记录支持的多个访问器"，在[用户记录](../data/oledb/user-records.md)。  
  
 当使用者特性提供程序应用于类时此属性时，编译器将该类重命名为\_*类名*访问器，其中*类名*是你为指定的名称类，并且编译器还将创建一个名为类*类名*，它派生自\_*类名*访问器。  将在类视图中看到这两个类。  
  
## <a name="example"></a>示例  
 下面的示例使用**db_accessor**将 Orders 表中的列分组从 Northwind 数据库到两个访问器。 访问器 0 是自动访问器中，并访问器 1 不是。  
  
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
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|特性块|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者特性](../windows/ole-db-consumer-attributes.md)   
