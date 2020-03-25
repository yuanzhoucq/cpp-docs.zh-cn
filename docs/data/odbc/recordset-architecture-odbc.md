---
title: 记录集：体系结构 (ODBC)
ms.date: 11/04/2016
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
ms.openlocfilehash: bb4b67a4c534598a8e26eb9ab5f297b108b67b6d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212987"
---
# <a name="recordset-architecture-odbc"></a>记录集：体系结构 (ODBC)

本主题适用于 MFC ODBC 类。

本主题介绍构成记录集对象的体系结构的数据成员：

- [字段数据成员](#_core_field_data_members)

- [参数数据成员](#_core_parameter_data_members)

- [使用 m_nFields 和 m_nParams 数据成员](#_core_using_m_nfields_and_m_nparams)

> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果实现批量提取行，体系结构则类似。 若要了解不同之处，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="sample-class"></a><a name="_core_a_sample_class"></a> 示例类

> [!NOTE]
> MFC ODBC 使用者向导在 Visual Studio 2019 及更高版本中不可用。 你仍可以手动创建使用者。

当你使用“添加类”向导中的 [MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)来声明从  **派生的记录集类时，生成的类具有以下简单类中所示的常规结构**`CRecordset`：

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

在类的开头，向导将编写一组[字段数据成员](#_core_field_data_members)。 创建类时，必须指定一个或多个字段数据成员。 如果像示例类一样类已参数化（带有数据成员 `m_strIDParam`），必须手动添加[参数数据成员](#_core_parameter_data_members)。 向导不支持向类添加参数。

##  <a name="field-data-members"></a><a name="_core_field_data_members"></a> 字段数据成员

记录集类最重要的成员是字段数据成员。 对于从数据源中选择的每个列，类将包含此列的相应数据类型的数据成员。 例如，本主题开头显示的[示例类](#_core_a_sample_class)有两个字段数据成员，类型为 `CString`，称为 `m_strCourseID` 和 `m_strCourseTitle`。

当记录集选择一组记录时，框架会自动将当前记录的列（在 `Open` 调用之后，第一条记录为当前记录）绑定到对象的字段数据成员。 也就是说，框架使用适当的字段数据成员作为缓冲区，用于存储记录列的内容。

当用户滚动到新记录时，框架将使用字段数据成员来表示当前记录。 框架将刷新字段数据成员，从而替换先前记录的值。 字段数据成员还用于更新当前记录和添加新记录。 作为更新记录过程的一部分，你可以通过将值直接分配给相应的字段数据成员来指定更新值。

##  <a name="parameter-data-members"></a><a name="_core_parameter_data_members"></a> 参数数据成员

如果类已参数化，它则有一个或多个参数数据成员。 参数化类使你能够将在运行时获取或计算的信息作为记录集查询的依据。

通常情况下，参数有助于缩小选择范围，如下例所示。 基于本主题开头的[示例类](#_core_a_sample_class)，记录集对象可能会执行以下 SQL 语句：

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?
```

“？”是你在运行时提供的参数值的占位符。 构造记录集并将其 `m_strIDParam` 数据成员设置为 MATH101 时，此记录集的有效 SQL 语句将变为：

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101
```

通过定义参数数据成员，你可以告知框架有关 SQL 字符串中参数的信息。 框架将绑定参数，使 ODBC 知道从何处获取值来替换占位符。 在此示例中，生成的记录集仅包含 Course 表中的记录，其中 CourseID 列的值为 MATH101。 此记录的所有指定列已被选中。 你可以根据需要指定任意数量的参数（以及占位符）。

> [!NOTE]
>  MFC 本身不处理参数，尤其是不执行文本替换。 相反，MFC 将告知 ODBC 从何处获取参数；ODBC 将检索数据并执行必要的参数化。

> [!NOTE]
>  参数的顺序很重要。 有关参数的信息和有关参数的详细信息，请参阅[记录集：参数化记录集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

##  <a name="using-m_nfields-and-m_nparams"></a><a name="_core_using_m_nfields_and_m_nparams"></a> 使用 m_nFields 和 m_nParams

当向导为类编写构造函数时，它还会初始化 [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) 数据成员，此成员指定类中[字段数据成员](#_core_field_data_members)的数量。 如果你向类中添加任何[参数](#_core_parameter_data_members)，还必须为 [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) 数据成员添加初始化，此成员指定参数数据成员的数量。 框架将使用这些值来处理数据成员。

有关详细信息和示例，请参阅[记录字段交换：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：声明表的类 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)
