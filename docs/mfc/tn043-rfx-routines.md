---
title: TN043：RFX 例程
ms.date: 06/28/2018
f1_keywords:
- RFX
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
ms.openlocfilehash: 278351ad1cf81215f4c6033f4cff0b100adedf23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658856"
---
# <a name="tn043-rfx-routines"></a>TN043：RFX 例程

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本说明介绍了记录字段交换 (RFX) 体系结构。 它还介绍了如何编写**RFX_** 过程。

## <a name="overview-of-record-field-exchange"></a>记录字段交换的概述

记录集字段的所有函数已都完成 c + + 代码。 没有任何特殊资源或神奇的宏。 该机制的核心是必须在每个派生的记录集类中重写虚函数。 它始终位于此窗体中：

```cpp
void CMySet::DoFieldExchange(CFieldExchange* pFX)
{
    //{{AFX_FIELD_MAP(CMySet)
        <recordset exchange field type call>
        <recordset exchange function call>
    //}}AFX_FIELD_MAP
}
```

特殊格式 AFX 评论功能允许 ClassWizard 定位和编辑此函数中的代码。 与 ClassWizard 不兼容的代码应放置在特殊格式注释之外。

在上述示例中， \<recordset_exchange_field_type_call > 的格式：

```cpp
pFX->SetFieldType(CFieldExchange::outputColumn);
```

和\<recordset_exchange_function_call > 的格式：

```cpp
RFX_Custom(pFX, "Col2", m_Col2);
```

大多数**RFX_** 函数具有三个参数，如上所示，但一些 (例如`RFX_Text`和`RFX_Binary`) 具有其他可选参数。

多个**RFX_** 可能包括在每个`DoDataExchange`函数。

请参阅 afxdb.h 有关的所有记录集字段 exchange 例程 MFC 提供的列表。

记录集字段调用是注册的内存位置 （通常是数据成员） 来存储字段的数据的方式`CMySet`类。

## <a name="notes"></a>说明

记录集字段函数用于处理仅`CRecordset`类。 它们不是通常可由任何其他 MFC 类。

标准 c + + 中的构造函数，通常具有的块中设置的数据的初始值`//{{AFX_FIELD_INIT(CMylSet)`和`//}}AFX_FIELD_INIT`注释。

每个**RFX_** 函数必须支持各种操作，范围从存档中准备用于编辑字段的字段返回该字段的更新状态。

每个函数都调用`DoFieldExchange`(例如`SetFieldNull`， `IsFieldDirty`)，执行其自己围绕对调用初始化`DoFieldExchange`。

## <a name="how-does-it-work"></a>它是如何工作的

不需要了解以下以使用记录字段交换。 但是，了解原理在后台将有助于您编写自己的 exchange 过程。

`DoFieldExchange`成员函数是非常类似于`Serialize`成员函数，它负责获取或设置数据向/从外部窗体 （在此事例的列从 ODBC 查询的结果） 从/向类中的成员数据。 *PFX*参数是执行数据交换的上下文，它是类似于*CArchive*参数`CObject::Serialize`。 *PFX* (`CFieldExchange`对象) 的操作标记，它是类似，但的泛化*CArchive*方向标志。 RFX 函数可能需要支持以下操作：

- `BindParam` 指示 ODBC 应在其中检索参数数据

- `BindFieldToColumn` 指示其中 ODBC 必须检索/存款 outputColumn 数据

- `Fixup` -设置`CString/CByteArray`长度设置为 NULL 状态位

- `MarkForAddNew` -如果值已更改，因为调用 AddNew，已更新标记

- `MarkForUpdate` -如果值已更改，因为编辑调用，已更新标记

- `Name` — 将附加字段标记为已更新的字段名称

- `NameValue` — 将追加"\<列名称 > ="标记为已更新的字段

- `Value` — 将追加""跟分隔符，如 '，' 或 '

- `SetFieldDirty` -设置状态位已更新 （即已更改） 字段

- `SetFieldNull` -设置字段的 null 值，该值指示的状态位

- `IsFieldDirty` -返回已更新的状态位的值

- `IsFieldNull` -返回 null 状态位的值

- `IsFieldNullable` — 如果字段可以包含 NULL 值，则返回 TRUE

- `StoreField` -存档字段值

- `LoadField` -重新加载已存档的字段值

- `GetFieldInfoValue` -返回的字段的常规信息

- `GetFieldInfoOrdinal` -返回的字段的常规信息

## <a name="user-extensions"></a>用户扩展

有几种方法来扩展默认 RFX 机制。 你可以

- 添加新的数据类型。 例如：

    ```cpp
    CBookmark
    ```

- 添加新的 exchange 过程 (RFX_)。

    ```cpp
    void AFXAPI RFX_Bigint(CFieldExchange* pFX,
        const char *szName,
        BIGINT& value);
    ```

- 具有`DoFieldExchange`成员函数有条件地包括其他 RFX 调用或任何其他有效的 c + + 语句。

    ```cpp
    while (posExtraFields != NULL)
    {
        RFX_Text(pFX,
        m_listName.GetNext(posExtraFields),
        m_listValue.GetNext(posExtraValues));
    }
    ```

> [!NOTE]
> 此类代码的类向导无法编辑，应使用仅之外的特殊格式的注释。

## <a name="writing-a-custom-rfx"></a>编写自定义 RFX

若要编写自己的自定义 RFX 函数，建议你复制现有 RFX 函数，并将它修改为根据自己的目的。 选择正确的 RFX 复制可以使您的工作更加轻松。 某些 RFX 函数具有一些在决定要复制时应考虑的唯一属性。

`RFX_Long` 和`RFX_Int`： 这些是最简单的 RFX 函数。 数据值不需要任何特殊的解释，以及数据大小固定的。

`RFX_Single` 和`RFX_Double`： 如 RFX_Long 和 RFX_Int 更高版本，这些函数很简单，可以使广泛使用的默认实现。 它们存储在 dbflt.cpp 而不是 dbrfx.cpp，但是，若要启用加载运行时的浮点库，仅在时显式引用。

`RFX_Text` 和`RFX_Binary`： 这两个函数预分配静态缓冲区来存放字符串/二进制文件的信息，并且必须向 ODBC SQLBindCol 注册这些缓冲区而不是注册 （& v）。 因此，这两个函数有很多特例代码。

`RFX_Date`: ODBC 返回自己 TIMESTAMP_STRUCT 数据结构中的日期和时间信息。 此函数为动态分配 TIMESTAMP_STRUCT"代理"作为发送和接收日期时间数据。 各种操作必须 c + + 之间传输的日期和时间信息`CTime`对象和 TIMESTAMP_STRUCT 代理。 这会增加复杂性此函数相当，但它是如何使用代理服务器进行数据传输的一个很好示例。

`RFX_LongBinary`： 这是唯一的类库 RFX 函数，不使用列绑定来接收和发送数据。 此函数将忽略 BindFieldToColumn 操作相反，在修复操作时，会分配存储区来存放传入 SQL_LONGVARCHAR 或 SQL_LONGVARBINARY 数据，然后执行 SQLGetData 呼叫将检索到的已分配存储的值。 当准备将发送回数据源 （如名称值和值的操作） 的数据值时，此函数将使用 ODBC 的 DATA_AT_EXEC 功能。 请参阅[技术说明 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)有关使用 SQL_LONGVARBINARY 和 SQL_LONGVARCHARs 的详细信息。

当编写你自己**RFX_** 函数，您通常将能够使用`CFieldExchange::Default`实现给定的操作。 查看相关操作在默认的实现。 如果执行该操作将需要你编写你**RFX_** 函数可以委派给`CFieldExchange::Default`。 你可以看到示例调用`CFieldExchange::Default`dbrfx.cpp 中

务必要调用`IsFieldType`开头的 RFX 函数，并且如果它返回 FALSE，则立即返回。 此机制会让参数上执行的操作*outputColumns*，反之亦然 (如调用`BindParam`上*outputColumn*)。 此外，`IsFieldType`自动跟踪的计数*outputColumns* (*m_nFields*) 以及参数 (*m_nParams*)。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
