---
title: db_accessor (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_accessor
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
ms.openlocfilehash: bfb287261fce4ebf189801c308f57513f2c9f113
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038299"
---
# <a name="dbaccessor"></a>db_accessor

组`db_column`参与属性`IAccessor`-基于绑定。

## <a name="syntax"></a>语法

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>参数

*num*<br/>
指定访问器数 （从零开始的整数索引）。 必须指定访问器中增加的数字顺序，使用整数，或者定义的值。

*auto*<br/>
一个布尔值，该值指定访问器是自动检索 (TRUE) 还是未检索到 (FALSE)。

## <a name="remarks"></a>备注

**db_accessor**定义为基础的 OLE DB 取值函数后续`db_column`和`db_param`相同类或函数中的属性。 **db_accessor**在成员级别为可用，并且使用到组`db_column`参与 OLE DB 属性`IAccessor`-基于绑定。 通过结合使用`db_table`或`db_command`属性。 调用此属性是类似于调用[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)并[END_ACCESSOR](../../data/oledb/end-accessor.md)宏。

**db_accessor**生成行集，并将其绑定到相应的访问器映射。 如果不调用**db_accessor**、 将自动生成访问器 0，和列的所有绑定将都映射到此访问器块。

**db_accessor**组数据库列绑定到一个或多个访问器。 您需要在其中使用多个访问器的方案的讨论，请参阅[行集上使用多个访问器](../../data/oledb/using-multiple-accessors-on-a-rowset.md)。 "用户记录的支持的多个访问器"中，还发现[用户记录](../../data/oledb/user-records.md)。

编译器时使用者特性提供程序适用于类，此属性，将重命名为类\_ *YourClassName*访问器，其中*名为 YourClassName*是您为指定的名称类和编译器还将创建一个名为类*名为 YourClassName*，它派生\_*名为 YourClassName*访问器。  将在类视图中看到这两个类。

## <a name="example"></a>示例

下面的示例使用**db_accessor**到订单表中两个访问器到 Northwind 数据库中的组列。 访问器 0 是一个自动访问器，并访问器 1 不是。

```cpp
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
|**必需的特性**|None|
|**无效的特性**|None|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[OLE DB 使用者特性](ole-db-consumer-attributes.md)