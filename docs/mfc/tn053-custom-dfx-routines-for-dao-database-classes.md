---
title: TN053：DAO 数据库类的自定义 DFX 例程
ms.date: 09/17/2019
helpviewer_keywords:
- MFC, DAO and
- database classes [MFC], DAO
- DAO [MFC], MFC
- DFX (DAO record field exchange) [MFC], custom routines
- TN053
- DAO [MFC], classes
- DFX (DAO record field exchange) [MFC]
- custom DFX routines [MFC]
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
ms.openlocfilehash: f7ad854f4dbb4e90c09e886c69260e4e2eea3be2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365263"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053：DAO 数据库类的自定义 DFX 例程

> [!NOTE]
> DAO 与 Access 数据库一起使用，并通过 Office 2013 支持。 DAO 3.6 是最终版本，它被视为过时版本。 可视化C++环境和向导不支持 DAO（尽管包含 DAO 类，您仍可以使用它们）。 Microsoft 建议您将[OLE DB 模板](../data/oledb/ole-db-templates.md)或[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)用于新项目。 您只应在维护现有应用程序时使用 DAO。

本技术说明描述了 DAO 记录字段交换 （DFX） 机制。 为了帮助了解 DFX 例程中发生的情况，该`DFX_Text`函数将作为示例详细解释。 作为本技术说明的其他信息来源，您可以检查其他单独的 DFX 函数的代码。 您可能不需要自定义 DFX 例程，因为可能需要自定义 RFX 例程（与 ODBC 数据库类一起使用）。

本技术说明包含：

- DFX 概述

- 使用 DAO 记录字段交换和动态绑定[的示例](#_mfcnotes_tn053_examples)

- [DFX 的工作原理](#_mfcnotes_tn053_how_dfx_works)

- [自定义 DFX 例程的作用](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [DFX_Text详情](#_mfcnotes_tn053_details_of_dfx_text)

**DFX 概述**

DAO 记录字段交换机制 （DFX） 用于简化使用`CDaoRecordset`类时检索和更新数据的过程。 使用`CDaoRecordset`类的数据成员简化了该过程。 通过派生从`CDaoRecordset`，可以将数据成员添加到派生类中，表示表或查询中的每个字段。 这种"静态绑定"机制很简单，但它可能不是所有应用程序的首选数据提取/更新方法。 每次更改当前记录时，DFX 都会检索每个绑定字段。 如果您正在开发一个性能敏感应用程序，在更改货币时不需要提取每个字段，则通过`CDaoRecordset::GetFieldValue`"动态绑定"，`CDaoRecordset::SetFieldValue`并且可能是首选的数据访问方法。

> [!NOTE]
> DFX 和动态绑定不是互斥的，因此可以使用静态和动态绑定的混合使用。

## <a name="example-1--use-of-dao-record-field-exchange-only"></a><a name="_mfcnotes_tn053_examples"></a>示例 1 = 仅使用 DAO 记录字段交换

（假设`CDaoRecordset`=`CMySet`派生类已打开）

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**示例 2 = 仅使用动态绑定**

（假设使用`CDaoRecordset`类`rs`，并且它已经打开）

```
// Add a new record to the customers table
COleVariant  varFieldValue1 (_T("MSFT"),
    VT_BSTRT);

//Note: VT_BSTRT flags string type as ANSI,
    instead of UNICODE default
COleVariant  varFieldValue2  (_T("Microsoft"),
    VT_BSTRT);

rs.AddNew();

rs.SetFieldValue(_T("Customer_ID"),
    varFieldValue1);

rs.SetFieldValue(_T("Customer_Name"),
    varFieldValue2);

rs.Update();
```

**示例 3 = 使用 DAO 记录字段交换和动态绑定**

（假设使用`CDaoRecordset`派生类`emp`浏览员工数据）

```
// Get the employee's data so that it can be displayed
emp.MoveNext();

// If user wants to see employee's photograph,
// fetch it
COleVariant varPhoto;
if (bSeePicture)
    emp.GetFieldValue(_T("photo"),
    varPhoto);

// Display the data
PopUpEmployeeData(emp.m_strFirstName,
    emp.m_strLastName,
    varPhoto);
```

## <a name="how-dfx-works"></a><a name="_mfcnotes_tn053_how_dfx_works"></a>DFX 的工作原理

DFX 机制的工作方式与 MFC ODBC 类使用的记录字段交换 （RFX） 机制类似。 DFX 和 RFX 的原则相同，但存在许多内部差异。 DFX 函数的设计使几乎所有代码都由各个 DFX 例程共享。 在最高级别的DFX只做几件事。

- 如有必要，DFX 构造 SQL **SELECT**子句和 SQL**参数S**子句。

- DFX 构造 DAO`GetRows`函数使用的绑定结构（稍后将对此进行更多讨论）。

- DFX 管理用于检测脏字段的数据缓冲区（如果使用双缓冲）

- DFX 管理**NULL**和 DIRTY 状态数组 **，** 并在必要时在更新时设置值。

DFX 机制的核心是`CDaoRecordset`派生类的功能。 `DoFieldExchange` 此函数调度对适当操作类型的单个 DFX 函数的调用。 在调用`DoFieldExchange`内部 MFC 函数之前，将设置操作类型。 下面的列表显示了各种操作类型和简要说明。

|Operation|说明|
|---------------|-----------------|
|`AddToParameterList`|生成参数子句|
|`AddToSelectList`|生成 SELECT 子句|
|`BindField`|设置绑定结构|
|`BindParam`|设置参数值|
|`Fixup`|设置 NULL 状态|
|`AllocCache`|为脏检查分配缓存|
|`StoreField`|将当前记录保存到缓存|
|`LoadField`|将缓存还原到成员值|
|`FreeCache`|释放缓存|
|`SetFieldNull`|将字段状态&值设置为 NULL|
|`MarkForAddNew`|将字段标记为脏，如果不是"无效"则|
|`MarkForEdit`|如果字段与缓存不匹配，则脏标记字段|
|`SetDirtyField`|设置标记为脏的字段值|

在下一节中，将更详细地解释 每个操作。 `DFX_Text`

了解 DAO 记录字段交换过程的最重要特征是它使用`GetRows``CDaoRecordset`对象的函数。 DAO`GetRows`函数可以通过多种方式工作。 本技术说明仅简要说明`GetRows`，因为它超出了本技术说明的范围。
DAO`GetRows`可以以多种方式工作。

- 它可以一次获取多个记录和多个数据字段。 这允许更快的数据访问，处理大型数据结构的复杂性，并相应偏移到每个字段和结构中的每个数据记录。 MFC 不会利用此多个记录提取机制。

- 另一`GetRows`种方法是允许程序员为一个数据记录为每个字段的检索数据指定绑定地址。

- DAO 还将"回拨"到调用方中，用于变量长度列，以便允许调用方分配内存。 第二个功能的好处是最大限度地减少数据拷贝的数量，并允许将数据直接存储到类的成员（`CDaoRecordset`派生类）。 第二种机制是 MFC 用于绑定到派生类中`CDaoRecordset`的数据成员的方法。

## <a name="what-your-custom-dfx-routine-does"></a><a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>自定义 DFX 例程的作用

从这个讨论中可以明显看出，任何DFX函数中实现的最重要操作必须是能够设置所需的数据结构才能成功调用`GetRows`。 DFX 函数还必须支持许多其他操作，但没有一个操作像正确准备`GetRows`调用那样重要或复杂。

在线文档中介绍了 DFX 的使用。 基本上，有两个要求。 首先，必须将成员添加到每个绑定`CDaoRecordset`字段和参数的派生类中。 之后`CDaoRecordset::DoFieldExchange`应重写。 请注意，成员的数据类型很重要。 它应该匹配数据库中的字段的数据，或者至少可转换为该类型。 例如，数据库中的数字字段（如长整数）始终可以转换为文本并绑定到`CString`成员，但数据库中的文本字段不一定转换为数字表示形式，如长整数并绑定到长整数成员。 DAO 和 Microsoft Jet 数据库引擎负责转换（而不是 MFC）。

## <a name="details-of-dfx_text"></a><a name="_mfcnotes_tn053_details_of_dfx_text"></a>DFX_Text详情

如前所述，解释 DFX 工作原理的最佳方法是通过示例工作。 为此，通过内部`DFX_Text`应很好地帮助提供对DFX的基本理解。

- `AddToParameterList`

   此操作将生成 Jet 所需的 SQL`Parameters <param name>, <param type> ... ;` **PARAMETERS**子句（""）。 每个参数都命名和键入（如 RFX 调用中指定）。 请参阅函数`CDaoFieldExchange::AppendParamType`函数以查看各个类型的名称。 在`DFX_Text`的情况下，使用的类型是**文本**。

- `AddToSelectList`

   生成 SQL **SELECT**子句。 这是相当直接的，因为 DFX 调用指定的列名称只是附加 （""）。`SELECT <column name>, ...`

- `BindField`

   最复杂的操作。 如前所述，这是设置所使用的`GetRows`DAO 绑定结构的位置。 正如您在`DFX_Text`结构中的信息类型中的代码中看到的，包括所使用的 DAO 类型（在 DAO_CHAR**DAO_CHAR**或**DAO_WCHAR**的情况下`DFX_Text`。 此外，还设置了使用的绑定类型。 在前面的一节中`GetRows`只简要地描述了这一点，但足以说明 MFC 使用的绑定类型始终是直接地址绑定 **（DAOBINDING_DIRECT**）。 此外，还使用可变长度列绑定（如`DFX_Text`） 回调绑定，以便 MFC 可以控制内存分配并指定正确长度的地址。 这意味着 MFC 始终可以告诉 DAO"将数据放在何处"，从而允许直接绑定到成员变量。 绑定结构的其余部分填充了内存分配回调函数的地址和列绑定的类型（按列名称绑定） 之类的内容。

- `BindParam`

   这是一个简单的操作，`SetParamValue`调用参数成员中指定的参数值。

- `Fixup`

   填写每个字段的**NULL**状态。

- `SetFieldNull`

   此操作仅将每个字段状态标记为**NULL，** 并将成员变量的值设置**为PSEUDO_NULL**。

- `SetDirtyField`

   调用`SetFieldValue`标记为脏的每个字段。

所有剩余的操作仅处理使用数据缓存。 数据缓存是当前记录中数据的额外缓冲区，用于使某些内容更简单。 例如，可以自动检测"脏"字段。 如在线文档中所述，它可以完全关闭，也可以在现场级别关闭。 缓冲区的实现使用映射。 此映射用于将动态分配的数据副本与"绑定"字段（或`CDaoRecordset`派生数据成员）的地址进行匹配。

- `AllocCache`

   动态分配缓存的字段值并将其添加到地图中。

- `FreeCache`

   删除缓存的字段值并将其从映射中删除。

- `StoreField`

   将当前字段值复制到数据缓存中。

- `LoadField`

   将缓存的值复制到字段成员中。

- `MarkForAddNew`

   检查当前字段值是否为非**NULL，** 并在必要时将其标记为脏。

- `MarkForEdit`

   将当前字段值与数据缓存进行比较，并在必要时标记脏值。

> [!TIP]
> 在现有 DFX 例程上为标准数据类型建模自定义 DFX 例程。

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
