---
title: 记录集： 体系结构 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, data members
- field data members, recordset architecture
- field data members
- m_nParams data member, recordsets
- recordsets, architecture
- parameter data members in recordsets
- m_nFields data member
- ODBC recordsets, architecture
- m_nParams data member
- m_nFields data member, recordsets
ms.assetid: 47555ddb-11be-4b9e-9b9a-f2931764d298
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e868e51acf4c4e8f3975010509a0c97799b5e38c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082198"
---
# <a name="recordset-architecture-odbc"></a>记录集：体系结构 (ODBC)

本主题适用于 MFC ODBC 类。

本主题描述包含记录集对象的体系结构的数据成员：

- [字段数据成员](#_core_field_data_members)

- [参数数据成员](#_core_parameter_data_members)

- [使用 m_nFields 和 m_nParams 数据成员](#_core_using_m_nfields_and_m_nparams)

> [!NOTE]
>  本主题适用于对象派生自`CRecordset`中的批量行提取尚未实现。 如果已实现批量行提取，体系结构是类似的。 若要了解的差异，请参阅[记录集： 提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="_core_a_sample_class"></a> 示例类

当你使用[MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)从**添加类**向导来声明一个记录集的类派生自`CRecordset`，所生成的类具有如下所示简单的一般结构类：

```cpp
class CCourse : public CRecordset
{
public:
   CCourse(CDatabase* pDatabase = NULL);
   ...
   CString m_strCourseID;
   CString m_strCourseTitle;
   CString m_strIDParam;
};
```

在类的开头，向导会将写入一系列[字段数据成员](#_core_field_data_members)。 在创建类时，必须指定一个或多个字段数据成员。 如果参数化类，示例类是 (与数据成员`m_strIDParam`)，则必须手动添加[的参数数据成员](#_core_parameter_data_members)。 该向导不支持向类添加参数。

##  <a name="_core_field_data_members"></a> 字段数据成员

最重要的记录集类成员是字段数据成员。 对于从数据源选择每个列，此类包含相应的数据类型为该列的数据成员。 例如，[示例类](#_core_a_sample_class)此开头所示主题具有两个字段数据成员，这两个类型`CString`称为`m_strCourseID`和`m_strCourseTitle`。

当该记录集选择的一组记录时，框架会自动将当前记录的列 (后`Open`调用时，第一条记录是最新) 到该对象的字段数据成员。 也就是说，框架将使用合适的字段数据成员作为要在其中存储记录列的内容缓冲区。

当用户滚动到新记录时，框架将使用的字段数据成员来表示当前记录。 在框架刷新替换上一条记录的值的字段数据成员。 更新当前记录以及添加新记录，也使用字段数据成员。 更新记录的过程的一部分，通过将值分配给合适的字段数据成员或成员直接指定的更新值。

##  <a name="_core_parameter_data_members"></a> 参数数据成员

如果类参数化，它具有一个或多个参数的数据成员。 参数化的类，可以基于获取，或在运行时计算的信息创建记录集查询。

通常情况下，该参数有助于缩小范围所选内容，如以下示例所示。 基于[示例类](#_core_a_sample_class)记录集对象可能会在本主题开始时，执行以下 SQL 语句：

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?
```

"？"是在运行时提供的参数值的占位符。 构造记录集时并设置其`m_strIDParam`MATH101 到的数据成员，该记录集的有效 SQL 语句将变为：

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101
```

通过定义的参数数据成员，您告诉框架 SQL 字符串中的参数。 框架绑定了参数，它使 ODBC 可以知道从何处获取的占位符值替换。 在示例中，生成的记录集包含仅具有其值是 MATH101 的 CourseID 列 Course 表中的记录。 选择此记录的所有指定的列。 可以指定任意数量的参数 （和占位符） 您可以根据需要。

> [!NOTE]
>  MFC 本身并不操作使用的参数，特别是，它不会执行文本替换。 相反，MFC 告知 ODBC 从中获取参数;ODBC 检索数据并执行必要的参数化。

> [!NOTE]
>  参数的顺序非常重要。 此类信息和参数详细信息，请参阅[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

##  <a name="_core_using_m_nfields_and_m_nparams"></a> 使用 m_nFields 和 m_nParams

当向导将为您的类的构造函数时，它还可以初始化[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)数据成员，指定的数[字段数据成员](#_core_field_data_members)类中。 如果添加任何[参数](#_core_parameter_data_members)到类，您还必须添加用于初始化[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)数据成员，用于指定参数数据成员的数目。 该框架使用这些值用于数据成员。

有关详细信息和示例，请参阅[记录字段交换： 使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：声明表的类 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)