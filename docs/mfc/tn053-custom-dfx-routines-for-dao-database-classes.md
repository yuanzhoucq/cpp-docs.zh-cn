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
ms.openlocfilehash: 6dde96520d9472726da86f8da295770cccc5d42c
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303440"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053：DAO 数据库类的自定义 DFX 例程

> [!NOTE]
>  DAO 与 Access 数据库结合使用，并受 Office 2013 的支持。 DAO 3.6 是最终版本，被视为已过时。 视觉对象C++环境和向导不支持 dao （尽管包含 dao 类，但你仍可以使用它）。 Microsoft 建议您对新项目使用 [OLE DB 模板](../data/oledb/ole-db-templates.md)或 [ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)。 只应在维护现有应用程序时使用 DAO。

本技术说明介绍了 DAO 记录字段交换（DFX）机制。 为了帮助了解 DFX 例程中发生的情况，将详细说明 `DFX_Text` 函数作为示例。 作为此技术说明的其他信息源，你可以检查其他每个 DFX 函数的代码。 您可能不需要自定义 DFX 例程，因为您可能需要自定义 RFX 例程（与 ODBC 数据库类一起使用）。

本技术说明包含：

- DFX 概述

- 使用 DAO 记录字段交换和动态绑定的[示例](#_mfcnotes_tn053_examples)

- [DFX 的工作方式](#_mfcnotes_tn053_how_dfx_works)

- [自定义 DFX 例程的作用](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [DFX_Text 的详细信息](#_mfcnotes_tn053_details_of_dfx_text)

**DFX 概述**

DAO 记录字段交换机制（DFX）用于在使用 `CDaoRecordset` 类时简化检索和更新数据的过程。 使用 `CDaoRecordset` 类的数据成员简化了该过程。 通过从 `CDaoRecordset`派生，你可以将数据成员添加到表示表或查询中的每个字段的派生类。 这种 "静态绑定" 机制很简单，但它可能不是所有应用程序的所选数据提取/更新方法。 每次更改当前记录时，DFX 都将检索每个绑定字段。 如果要开发一个性能敏感的应用程序，该应用程序在货币更改时不需要提取每个字段，则通过 `CDaoRecordset::GetFieldValue` 和 `CDaoRecordset::SetFieldValue` "动态绑定" 可能是选择的数据访问方法。

> [!NOTE]
>  DFX 和动态绑定并不互相排斥，因此可以使用静态和动态绑定的混合使用。

## <a name="_mfcnotes_tn053_examples"></a>示例 1-仅使用 DAO 记录字段交换

（假定 `CDaoRecordset`：派生类 `CMySet` 已打开）

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**示例 2-仅使用动态绑定**

（假定使用 `CDaoRecordset` 类，`rs`并已打开）

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

**示例 3-使用 DAO 记录字段交换和动态绑定**

（假定浏览 `CDaoRecordset`派生类 `emp`的员工数据）

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

## <a name="_mfcnotes_tn053_how_dfx_works"></a>DFX 的工作方式

DFX 机制的工作方式类似于 MFC ODBC 类使用的记录字段交换（RFX）机制。 DFX 和 RFX 的原则相同，但有许多内部差异。 DFX 函数的设计是指几乎所有代码都由各个 DFX 例程共享。 在最高级别，DFX 仅执行几项任务。

- 如果需要，DFX 将构造 SQL **SELECT**子句和 sql**参数**子句。

- DFX 构造 DAO 的 `GetRows` 函数使用的绑定结构（稍后将对此进行详细介绍）。

- DFX 管理用于检测脏字段（如果正在使用双缓冲）的数据缓冲区

- DFX 管理**NULL**和**DIRTY**状态数组，并在更新时设置值。

DFX 机制的核心是 `CDaoRecordset` 派生类的 `DoFieldExchange` 函数。 此函数将调用调度到相应操作类型的单个 DFX 函数。 在调用 `DoFieldExchange` 内部 MFC 函数之前，请设置操作类型。 以下列表显示了各种操作类型和简短说明。

|操作|描述|
|---------------|-----------------|
|`AddToParameterList`|Build PARAMETERS 子句|
|`AddToSelectList`|生成 SELECT 子句|
|`BindField`|设置绑定结构|
|`BindParam`|设置参数值|
|`Fixup`|设置 NULL 状态|
|`AllocCache`|为脏检查分配缓存|
|`StoreField`|将当前记录保存到缓存|
|`LoadField`|将缓存还原到成员值|
|`FreeCache`|释放缓存|
|`SetFieldNull`|将字段状态 & 值设置为 NULL|
|`MarkForAddNew`|如果不是伪 NULL，则将字段标记为脏|
|`MarkForEdit`|如果不匹配缓存，则标记字段的更新|
|`SetDirtyField`|设置标记为已更新的字段值|

在下一部分中，将更详细地说明每个操作的 `DFX_Text`。

了解 DAO 记录字段交换过程的最重要的功能是使用 `CDaoRecordset` 对象的 `GetRows` 函数。 DAO `GetRows` 函数可以通过多种方式工作。 本技术说明将仅对 `GetRows` 进行简要描述，因为它不在本技术说明的讨论范围内。
DAO `GetRows` 可以通过多种方式工作。

- 它可以一次提取多个记录和多个字段。 这样，就可以更快地访问数据，同时处理大型数据结构，并为结构中的每个字段和每个数据记录提供相应的偏移量。 MFC 不利用此多记录提取机制。

- `GetRows` 的另一种方法是允许程序员为数据的每个字段的检索数据指定绑定地址。

- DAO 还向调用方提供可变长度列，以允许调用方分配内存。 第二个功能的优点是最大限度地减少了数据副本的数量，并允许将数据直接存储到类（`CDaoRecordset` 派生类）的成员中。 第二种机制是 MFC 用于绑定到 `CDaoRecordset` 派生类中的数据成员的方法。

##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>自定义 DFX 例程的作用

在此讨论中，在任何 DFX 函数中实现的最重要的操作都必须能够设置所需的数据结构，才能成功调用 `GetRows`。 DFX 函数还必须支持其他一些操作，但对于 `GetRows` 调用的正确准备，并没有任何重要或复杂的操作。

联机文档中介绍了如何使用 DFX。 实质上，有两个要求。 首先，必须将成员添加到每个绑定字段和参数的 `CDaoRecordset` 派生类中。 应覆盖以下 `CDaoRecordset::DoFieldExchange`。 请注意，成员的数据类型非常重要。 它应该与数据库中字段的数据匹配，或者至少能够转换为该类型。 例如，数据库中的数字字段（如长整数）始终可以转换为文本并绑定到 `CString` 成员，但是数据库中的文本字段可能不一定转换为数值表示形式，如 long 整数和绑定到长整数成员。 DAO 和 Microsoft Jet 数据库引擎负责转换（而不是 MFC）。

##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a>DFX_Text 的详细信息

如前所述，解释 DFX 工作方式的最佳方式是通过示例。 出于此目的，通过 `DFX_Text` 的内部工作原理应该非常好，有助于至少提供对 DFX 的基本了解。

- `AddToParameterList`

   此操作生成 Jet 所需的 SQL**参数**子句（"`Parameters <param name>, <param type> ... ;`"）。 每个参数的名称和类型（在 RFX 调用中指定）。 请参阅函数 `CDaoFieldExchange::AppendParamType` 函数，查看各个类型的名称。 如果是 `DFX_Text`，则使用的类型为**text**。

- `AddToSelectList`

   生成 SQL **SELECT**子句。 这相当简单，因为 DFX 调用指定的列名称只追加了（"`SELECT <column name>, ...`"）。

- `BindField`

   最复杂的操作。 如前所述，这是 `GetRows` 所使用的 DAO 绑定结构。 从 `DFX_Text` 中的代码中可以看到，结构中的信息类型包括所使用的 DAO 类型（在 `DFX_Text`情况下为**DAO_CHAR**或**DAO_WCHAR** ）。 此外，还设置了所使用的绑定类型。 在前面的部分中，`GetRows` 只是短暂说明，但足以说明 MFC 使用的绑定类型始终是直接地址绑定（**DAOBINDING_DIRECT**）。 此外，还使用可变长度列绑定（如 `DFX_Text`）回调绑定，以便 MFC 可以控制内存分配，并指定正确长度的地址。 这意味着 MFC 始终可以指示 DAO "where" 放置数据，从而允许直接绑定到成员变量。 绑定结构的其余部分填入了内存分配回调函数的地址和列绑定的类型（按列名绑定）等内容。

- `BindParam`

   这是一个简单的操作，用参数成员中指定的参数值调用 `SetParamValue`。

- `Fixup`

   填充每个字段的**NULL**状态。

- `SetFieldNull`

   此操作仅将每个字段状态标记为**NULL** ，并将成员变量的值设置为**PSEUDO_NULL**。

- `SetDirtyField`

   调用标记为 "已更新" 的每个字段 `SetFieldValue`。

所有剩余操作仅处理数据缓存。 数据缓存是当前记录中数据的额外缓冲区，用来使某些功能变得更简单。 例如，可以自动检测到 "更新" 的字段。 如联机文档中所述，可以完全关闭或在字段级别关闭。 缓冲区的实现利用映射。 此映射用于将数据的动态分配副本与 "绑定" 字段（或 `CDaoRecordset` 派生数据成员）的地址进行匹配。

- `AllocCache`

   动态分配缓存的字段值，并将其添加到地图中。

- `FreeCache`

   删除缓存的字段值并将其从映射中删除。

- `StoreField`

   将当前字段值复制到数据缓存中。

- `LoadField`

   将缓存的值复制到字段成员。

- `MarkForAddNew`

   检查当前字段值是否为非**NULL** ，并在必要时将其标记为已更新。

- `MarkForEdit`

   将当前字段值与数据缓存进行比较，并在必要时标记为已更新。

> [!TIP]
> 对标准数据类型的现有 DFX 例程的自定义 DFX 例程建模。

## <a name="see-also"></a>另请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
