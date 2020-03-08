---
title: CDaoTableDef 类
ms.date: 11/04/2016
f1_keywords:
- CDaoTableDef
- AFXDAO/CDaoTableDef
- AFXDAO/CDaoTableDef::CDaoTableDef
- AFXDAO/CDaoTableDef::Append
- AFXDAO/CDaoTableDef::CanUpdate
- AFXDAO/CDaoTableDef::Close
- AFXDAO/CDaoTableDef::Create
- AFXDAO/CDaoTableDef::CreateField
- AFXDAO/CDaoTableDef::CreateIndex
- AFXDAO/CDaoTableDef::DeleteField
- AFXDAO/CDaoTableDef::DeleteIndex
- AFXDAO/CDaoTableDef::GetAttributes
- AFXDAO/CDaoTableDef::GetConnect
- AFXDAO/CDaoTableDef::GetDateCreated
- AFXDAO/CDaoTableDef::GetDateLastUpdated
- AFXDAO/CDaoTableDef::GetFieldCount
- AFXDAO/CDaoTableDef::GetFieldInfo
- AFXDAO/CDaoTableDef::GetIndexCount
- AFXDAO/CDaoTableDef::GetIndexInfo
- AFXDAO/CDaoTableDef::GetName
- AFXDAO/CDaoTableDef::GetRecordCount
- AFXDAO/CDaoTableDef::GetSourceTableName
- AFXDAO/CDaoTableDef::GetValidationRule
- AFXDAO/CDaoTableDef::GetValidationText
- AFXDAO/CDaoTableDef::IsOpen
- AFXDAO/CDaoTableDef::Open
- AFXDAO/CDaoTableDef::RefreshLink
- AFXDAO/CDaoTableDef::SetAttributes
- AFXDAO/CDaoTableDef::SetConnect
- AFXDAO/CDaoTableDef::SetName
- AFXDAO/CDaoTableDef::SetSourceTableName
- AFXDAO/CDaoTableDef::SetValidationRule
- AFXDAO/CDaoTableDef::SetValidationText
- AFXDAO/CDaoTableDef::m_pDAOTableDef
- AFXDAO/CDaoTableDef::m_pDatabase
helpviewer_keywords:
- CDaoTableDef [MFC], CDaoTableDef
- CDaoTableDef [MFC], Append
- CDaoTableDef [MFC], CanUpdate
- CDaoTableDef [MFC], Close
- CDaoTableDef [MFC], Create
- CDaoTableDef [MFC], CreateField
- CDaoTableDef [MFC], CreateIndex
- CDaoTableDef [MFC], DeleteField
- CDaoTableDef [MFC], DeleteIndex
- CDaoTableDef [MFC], GetAttributes
- CDaoTableDef [MFC], GetConnect
- CDaoTableDef [MFC], GetDateCreated
- CDaoTableDef [MFC], GetDateLastUpdated
- CDaoTableDef [MFC], GetFieldCount
- CDaoTableDef [MFC], GetFieldInfo
- CDaoTableDef [MFC], GetIndexCount
- CDaoTableDef [MFC], GetIndexInfo
- CDaoTableDef [MFC], GetName
- CDaoTableDef [MFC], GetRecordCount
- CDaoTableDef [MFC], GetSourceTableName
- CDaoTableDef [MFC], GetValidationRule
- CDaoTableDef [MFC], GetValidationText
- CDaoTableDef [MFC], IsOpen
- CDaoTableDef [MFC], Open
- CDaoTableDef [MFC], RefreshLink
- CDaoTableDef [MFC], SetAttributes
- CDaoTableDef [MFC], SetConnect
- CDaoTableDef [MFC], SetName
- CDaoTableDef [MFC], SetSourceTableName
- CDaoTableDef [MFC], SetValidationRule
- CDaoTableDef [MFC], SetValidationText
- CDaoTableDef [MFC], m_pDAOTableDef
- CDaoTableDef [MFC], m_pDatabase
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
ms.openlocfilehash: 485fe3533916e5e59bc87084f58acfb37368ac32
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883859"
---
# <a name="cdaotabledef-class"></a>CDaoTableDef 类

表示基表或附加表的已存储定义。

## <a name="syntax"></a>语法

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|构造 `CDaoTableDef` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDaoTableDef：： Append](#append)|将新表添加到数据库。|
|[CDaoTableDef::CanUpdate](#canupdate)|如果可以更新表，则返回非零值（您可以修改字段或表属性的定义）。|
|[CDaoTableDef：： Close](#close)|关闭打开的 tabledef。|
|[CDaoTableDef：： Create](#create)|创建可使用[Append](#append)添加到数据库中的表。|
|[CDaoTableDef::CreateField](#createfield)|调用以创建表的字段。|
|[CDaoTableDef：： CreateIndex](#createindex)|调用以创建表的索引。|
|[CDaoTableDef：:D eleteField](#deletefield)|调用以从表中删除字段。|
|[CDaoTableDef：:D eleteIndex](#deleteindex)|调用以从表中删除索引。|
|[CDaoTableDef：： GetAttributes](#getattributes)|返回一个值，该值指示 `CDaoTableDef` 对象的一个或多个特性。|
|[CDaoTableDef：： GetConnect](#getconnect)|返回一个值，该值提供有关表的源的信息。|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|返回创建 `CDaoTableDef` 对象基础的基础表的日期和时间。|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|返回对基表设计所做的最新更改的日期和时间。|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|返回一个值，该值表示表中的字段数。|
|[CDaoTableDef：： Issomapper.getfieldinfo](#getfieldinfo)|返回有关表中的字段的特定类型的信息。|
|[CDaoTableDef::GetIndexCount](#getindexcount)|返回表的索引数。|
|[CDaoTableDef：： GetIndexInfo](#getindexinfo)|返回有关表的索引的特定类型的信息。|
|[CDaoTableDef：： GetName](#getname)|返回表的用户定义名称。|
|[CDaoTableDef：： GetRecordCount](#getrecordcount)|返回表中的记录数。|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|返回一个值，该值指定源数据库中附加表的名称。|
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|返回一个值，该值在字段更改或添加到表中时对其数据进行验证。|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|返回一个值，该值指定当字段对象的值不满足指定的验证规则时，应用程序显示的消息文本。|
|[CDaoTableDef：： IsOpen](#isopen)|如果表为打开状态，则返回非零值。|
|[CDaoTableDef：： Open](#open)|打开数据库的 TableDef's 集合中存储的现有 tabledef。|
|[CDaoTableDef::RefreshLink](#refreshlink)|更新附加表的连接信息。|
|[CDaoTableDef：： SetAttributes](#setattributes)|设置一个值，该值指示 `CDaoTableDef` 对象的一个或多个特性。|
|[CDaoTableDef::SetConnect](#setconnect)|设置一个值，该值提供有关表的源的信息。|
|[CDaoTableDef：： SetName](#setname)|设置表的名称。|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|设置一个值，该值指定源数据库中附加表的名称。|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|设置一个值，该值在字段更改或添加到表中时对其数据进行验证。|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|设置一个值，该值指定当字段对象的值不满足指定的验证规则时，应用程序显示的消息文本。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CDaoTableDef：： m_pDAOTableDef](#m_pdaotabledef)|指向 tabledef 对象基础的 DAO 接口的指针。|
|[CDaoTableDef：： m_pDatabase](#m_pdatabase)|此表的源数据库。|

## <a name="remarks"></a>备注

每个 DAO 数据库对象维护一个名为 TableDefs 的集合，其中包含所有已保存的 DAO tabledef 对象。

使用 `CDaoTableDef` 对象操作表定义。 例如，你能够：

- 检查数据库中任何本地表、附加表或外部表的字段和索引结构。

- 为附加的表调用 `SetConnect` 和 `SetSourceTableName` 成员函数，并使用 `RefreshLink` 成员函数更新与附加表的连接。

- 调用 `CanUpdate` 成员函数以确定是否可以编辑表中的字段定义。

- 使用 `GetValidationRule` 和 `SetValidationRule`获取或设置验证条件，以及 `GetValidationText` 和 `SetValidationText` 成员函数。

- 使用 `Open` 成员函数创建 `CDaoRecordset` 对象的表、动态集或快照类型。

    > [!NOTE]
    >  DAO 数据库类与基于开放式数据库连接（ODBC）的 MFC 数据库类不同。 所有 DAO 数据库类名称都具有 "CDao" 前缀。 你仍可以使用 DAO 类访问 ODBC 数据源;DAO 类通常提供了高级功能，因为它们特定于 Microsoft Jet 数据库引擎。

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>使用 tabledef 对象来处理现有表或创建新表

1. 在所有情况下，首先构造一个 `CDaoTableDef` 对象，并提供指向该表所属的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象的指针。

1. 然后根据需要执行以下操作：

   - 若要使用现有的已保存表，请调用 tabledef 对象的[Open](#open)成员函数，同时提供已保存表的名称。

   - 若要创建新表，请调用 tabledef 对象的[create](#create)成员函数，同时提供该表的名称。 调用[CreateField](#createfield)和[CreateIndex](#createindex)以向表中添加字段和索引。

   - 调用[Append](#append)以保存表，方法是将其追加到数据库的 TableDefs 集合。 `Create` 将 tabledef 置于打开状态，因此在调用 `Create` 不调用 `Open`。

        > [!TIP]
        >  创建保存的表的最简单方法是使用 Microsoft Access 创建并将其存储在数据库中。 然后，你可以在 MFC 代码中打开和使用它们。

若要使用已打开或创建的 tabledef 对象，请创建并打开 `CDaoRecordset` 对象，并使用*nOpenType*参数中的 `dbOpenTable` 值指定 tabledef 的名称。

若要使用 tabledef 对象创建 `CDaoRecordset` 对象，通常按上述方式创建或打开 tabledef，然后构造 recordset 对象，并在调用[CDaoRecordset：： open](../../mfc/reference/cdaorecordset-class.md#open)时将指针传递到 tabledef 对象。 传递的 tabledef 必须处于打开状态。 有关详细信息，请参阅类[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

完成使用 tabledef 对象后，调用其[Close](../../mfc/reference/cdaorecordset-class.md#close)成员函数;然后销毁 tabledef 对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>要求

**标头：** afxdao

##  <a name="append"></a>CDaoTableDef：： Append

调用[create](#create)后调用此成员函数以创建新的 tabledef 对象，以将 tabledef 保存在数据库中。

```
virtual void Append();
```

### <a name="remarks"></a>备注

函数将对象追加到数据库的 TableDefs 集合。 你可以使用 tabledef 作为临时对象，但通过不追加来定义它，但如果要保存和使用它，则必须调用 `Append`。

> [!NOTE]
>  如果尝试追加未命名的 tabledef （包含 null 或空字符串），MFC 将引发异常。

有关相关信息，请参阅 DAO 帮助中的主题 "Append 方法"。

##  <a name="canupdate"></a>CDaoTableDef::CanUpdate

调用此成员函数以确定是否可以更改 `CDaoTableDef` 对象基础的表的定义。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>返回值

如果可以修改表结构（架构），则为非零值，否则为0。

### <a name="remarks"></a>备注

默认情况下，可以更新 `CDaoTableDef` 对象基础上的新创建的表，不能更新基于 `CDaoTableDef` 对象的附加表。 即使生成的记录集不可更新，也可以更新 `CDaoTableDef` 对象。

有关相关信息，请参阅 DAO 帮助中的主题 "可更新属性"。

##  <a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef

构造 `CDaoTableDef` 对象。

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>参数

*pDatabase*<br/>
指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象的指针。

### <a name="remarks"></a>备注

构造对象之后，必须调用[Create](#create)或[Open](#open)成员函数。 当你完成对象时，必须调用其[Close](#close)成员函数并销毁 `CDaoTableDef` 的对象。

##  <a name="close"></a>CDaoTableDef：： Close

调用此成员函数以关闭并释放 tabledef 对象。

```
virtual void Close();
```

### <a name="remarks"></a>备注

通常在调用 `Close`后，如果 tabledef 对象是用**new**分配的，则将其删除。

调用 `Close`后，可以再次调用[Open](#open) 。 这使你可以重复使用 tabledef 对象。

有关相关信息，请参阅 DAO 帮助中的主题 "关闭方法"。

##  <a name="create"></a>CDaoTableDef：： Create

调用此成员函数以创建新的已保存表。

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
指向包含表名称的字符串的指针。

*lAttributes*<br/>
一个值，该值对应于 tabledef 对象所表示的表的特征。 您可以使用按位 "或" 组合以下任意常量：

|常量|说明|
|--------------|-----------------|
|`dbAttachExclusive`|对于使用 Microsoft Jet 数据库引擎的数据库，指示表是一个打开以供独占使用的附加表。|
|`dbAttachSavePWD`|对于使用 Microsoft Jet 数据库引擎的数据库，指示附加表的用户 ID 和密码与连接信息一起保存。|
|`dbSystemObject`|指示表是由 Microsoft Jet 数据库引擎提供的系统表。|
|`dbHiddenObject`|指示表是由 Microsoft Jet 数据库引擎提供的隐藏表。|

*lpszSrcTable*<br/>
指向包含源表名称的字符串的指针。 默认情况下，此值初始化为 NULL。

*lpszConnect*<br/>
指向包含默认连接字符串的字符串的指针。 默认情况下，此值初始化为 NULL。

### <a name="remarks"></a>备注

命名 tabledef 后，可以调用[Append](#append)将 tabledef 保存在数据库的 TableDefs 集合中。 调用 `Append`后，tabledef 处于打开状态，你可以使用它来创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。

有关相关信息，请参阅 DAO 帮助中的 "CreateTableDef 方法" 主题。

##  <a name="createfield"></a>CDaoTableDef::CreateField

调用此成员函数可向表中添加字段。

```
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
一个指针，指向用于指定此字段的名称的字符串表达式。

nType<br/>
指示字段的数据类型的值。 该设置可以是下列值之一：

|类型|大小(字节)|说明|
|----------|--------------------|-----------------|
|`dbBoolean`|1 个字节|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|货币（ [COleCurrency](../../mfc/reference/colecurrency-class.md)）|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|日期/时间（ [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)）|
|`dbText`|1 - 255|文本（ [CString](../../atl-mfc-shared/reference/cstringt-class.md)）|
|`dbLongBinary`|0|Long Binary （OLE 对象）、 [CLongBinary](../../mfc/reference/clongbinary-class.md)或[CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|备注（ [CString](../../atl-mfc-shared/reference/cstringt-class.md)）|

*lSize*<br/>
一个值，该值指示包含文本的字段的最大大小（以字节为单位）或包含文本或数字值的字段的固定大小。 对于除文本字段之外的所有文本，将忽略*lSize*参数。

*lAttributes*<br/>
与字段的特性对应的值，可以使用按位 "或" 进行组合。

|常量|说明|
|--------------|-----------------|
|`dbFixedField`|字段大小是固定的（数值字段的默认值）。|
|`dbVariableField`|字段大小是可变的（仅限文本字段）。|
|`dbAutoIncrField`|新记录的字段值会自动递增为一个唯一的长整数，该整数不能更改。 仅支持 Microsoft Jet 数据库表。|
|`dbUpdatableField`|可以更改该字段的值。|
|`dbDescending`|字段按降序（Z-a 或 100-0）排序（仅适用于索引对象的字段集合中的 Field 对象）。 如果省略此常量，则字段将按升序（A-z 或 0-100）排序（默认值）。|

*fieldinfo*<br/>
对[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构的引用。

### <a name="remarks"></a>备注

创建 `DAOField` （OLE）对象并将其追加到 `DAOTableDef` （OLE）对象的字段集合。 除了用于检查对象属性之外，还可以使用 `CDaoFieldInfo` 来构造用于在 tabledef 中创建新字段的输入参数。 `CreateField` 的第一个版本更简单，但如果您需要更精细的控制，则可以使用 `CreateField`的第二个版本，该版本采用 `CDaoFieldInfo` 参数。

如果使用采用 `CDaoFieldInfo` 参数的 `CreateField` 版本，则必须仔细设置 `CDaoFieldInfo` 结构的以下每个成员：

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

`CDaoFieldInfo` 的其余成员应设置为**0**、FALSE 或空字符串（如果适用于成员），否则可能会发生 `CDaoException`。

有关相关信息，请参阅 DAO 帮助中的 "CreateField 方法" 主题。

##  <a name="createindex"></a>CDaoTableDef：： CreateIndex

调用此函数可向表中添加索引。

```
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>参数

*indexinfo*<br/>
对[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构的引用。

### <a name="remarks"></a>备注

索引指定从数据库表中访问记录的顺序，以及是否接受重复记录。 索引还提供对数据的有效访问。

您不必为表创建索引，但是在大型的、未索引的表中，访问特定记录或创建记录集可能需要很长时间。 另一方面，创建太多索引会减缓更新、追加和删除操作的速度，因为所有索引会自动更新。 在决定要创建哪些索引时，请考虑以下因素。

必须设置 `CDaoIndexInfo` 结构的以下成员：

- 必须提供 `m_strName` 名称。

- `m_pFieldInfos` 必须指向 `CDaoIndexFieldInfo` 结构的数组。

- `m_nFields` 必须指定 `CDaoFieldInfo` 结构的数组中的字段数。

如果设置为 FALSE，则忽略剩余的成员。 此外，在索引创建过程中将忽略 `m_lDistinctCount` 成员。

##  <a name="deletefield"></a>CDaoTableDef：:D eleteField

调用此成员函数以删除字段并使其不可访问。

```
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
一个指针，指向作为现有字段的名称的字符串表达式。

*nIndex*<br/>
表的从零开始的字段集合中的字段索引，用于按索引查找。

### <a name="remarks"></a>备注

您可以对尚未追加到数据库或[CanUpdate](#canupdate)返回非零值的新对象使用此成员函数。

有关相关信息，请参阅 DAO 帮助中的 "删除方法" 主题。

##  <a name="deleteindex"></a>CDaoTableDef：:D eleteIndex

调用此成员函数可删除基础表中的索引。

```
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
一个指针，指向作为现有索引的名称的字符串表达式。

*nIndex*<br/>
数据库的从零开始的 TableDefs 集合中的索引对象的数组索引，用于按索引查找。

### <a name="remarks"></a>备注

您可以对尚未追加到数据库或[CanUpdate](#canupdate)返回非零值的新对象使用此成员函数。

有关相关信息，请参阅 DAO 帮助中的 "删除方法" 主题。

##  <a name="getattributes"></a>CDaoTableDef：： GetAttributes

对于 `CDaoTableDef` 对象，返回值指定由 `CDaoTableDef` 对象表示的表的特征，可以是以下常量的总和：

```
long GetAttributes();
```

### <a name="return-value"></a>返回值

返回一个值，该值指示 `CDaoTableDef` 对象的一个或多个特性。

### <a name="remarks"></a>备注

|常量|说明|
|--------------|-----------------|
|`dbAttachExclusive`|对于使用 Microsoft Jet 数据库引擎的数据库，指示表是一个打开以供独占使用的附加表。|
|`dbAttachSavePWD`|对于使用 Microsoft Jet 数据库引擎的数据库，指示附加表的用户 ID 和密码与连接信息一起保存。|
|`dbSystemObject`|指示表是由 Microsoft Jet 数据库引擎提供的系统表。|
|`dbHiddenObject`|指示表是由 Microsoft Jet 数据库引擎提供的隐藏表。|
|`dbAttachedTable`|指示表是来自非 ODBC 数据库（如 Paradox 数据库）的附加表。|
|`dbAttachedODBC`|指示表是来自 ODBC 数据库的附加表，如 Microsoft SQL Server。|

系统表是由 Microsoft Jet 数据库引擎创建的表，包含各种内部信息。

隐藏表是由 Microsoft Jet 数据库引擎暂时使用而创建的表。

有关相关信息，请参阅 DAO 帮助中的 "属性属性" 主题。

##  <a name="getconnect"></a>CDaoTableDef：： GetConnect

调用此成员函数以获取数据源的连接字符串。

```
CString GetConnect();
```

### <a name="return-value"></a>返回值

一个 `CString` 对象，该对象包含表的路径和数据库类型。

### <a name="remarks"></a>备注

对于表示附加表的 `CDaoTableDef` 对象，`CString` 对象包含一个或两个部分（数据库类型说明符和数据库的路径）。

下表中所示的路径是包含数据库文件的目录的完整路径，必须在其前面加上标识符 "DATABASE ="。 在某些情况下（与 Microsoft Jet 和 Microsoft Excel 数据库一样），数据库路径参数中包含特定的文件名。

[CDaoTableDef：： SetConnect](#setconnect)中的表显示了可能的数据库类型及其相应的数据库说明符和路径：

对于 Microsoft Jet 数据库基表，说明符为空字符串（""）。

如果需要密码，但未提供，则在首次访问表时，ODBC 驱动程序将显示一个登录对话框，如果连接已关闭并重新打开，则为。 如果附加表具有 `dbAttachSavePWD` 属性，则重新打开该表时，将不会显示登录提示。

相关信息，请参阅 DAO 帮助中的 "连接属性" 主题。

##  <a name="getdatecreated"></a>CDaoTableDef::GetDateCreated

调用此函数可确定创建 `CDaoTableDef` 对象基础的表的日期和时间。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>返回值

一个值，该值包含创建 `CDaoTableDef` 对象基础的表的日期和时间。

### <a name="remarks"></a>备注

日期和时间设置派生自创建或上次更新基表的计算机。 在多用户环境中，用户应直接从文件服务器获取这些设置，以避免差异;也就是说，所有客户端都应该使用一台服务器上的 "标准" 时间源。

相关信息，请参阅 DAO 帮助中的主题 "DateCreated，LastUpdated Properties"。

##  <a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated

调用此函数可确定上次更新 `CDaoTableDef` 对象所基于的表的日期和时间。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>返回值

一个值，该值包含上次更新 `CDaoTableDef` 对象所基于的表的日期和时间。

### <a name="remarks"></a>备注

日期和时间设置派生自创建或上次更新基表的计算机。 在多用户环境中，用户应直接从文件服务器获取这些设置，以避免差异;也就是说，所有客户端都应该使用一台服务器上的 "标准" 时间源。

相关信息，请参阅 DAO 帮助中的主题 "DateCreated，LastUpdated Properties"。

##  <a name="getfieldcount"></a>CDaoTableDef::GetFieldCount

调用此成员函数以检索表中定义的字段数。

```
short GetFieldCount();
```

### <a name="return-value"></a>返回值

表中的字段数。

### <a name="remarks"></a>备注

如果其值为0，则集合中不存在任何对象。

相关信息，请参阅 DAO 帮助中的 "计数属性" 主题。

##  <a name="getfieldinfo"></a>CDaoTableDef：： Issomapper.getfieldinfo

调用此成员函数可获取有关在 tabledef 中定义的字段的各种信息。

```
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
表的从零开始的字段集合中字段对象的索引，用于按索引查找。

*fieldinfo*<br/>
对[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构的引用。

*dwInfoOptions*<br/>
用于指定要检索的字段信息的选项。 此处列出了可用的选项，以及它们导致函数返回的内容：

- `AFX_DAO_PRIMARY_INFO` （默认值）名称、类型、大小、特性。 使用此选项以实现最高性能。

- `AFX_DAO_SECONDARY_INFO` 主要信息，加上：序号位置，必需，允许零长度，排序顺序，外名称，源字段，源表

- `AFX_DAO_ALL_INFO` 主要和辅助信息，以及：验证规则、验证文本、默认值

*lpszName*<br/>
一个指针，指向字段对象的名称，用于按名称进行查找。 该名称是一个字符串，其中最多可64对字段进行唯一命名。

### <a name="remarks"></a>备注

函数的一个版本允许您按索引查找字段。 其他版本允许您按名称查找字段。

有关所返回信息的说明，请参阅[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 此结构中有与*dwInfoOptions*中的说明中列出的信息项对应的成员。 当你在一个级别请求信息时，还会获取任何以前的级别的信息。

有关相关信息，请参阅 DAO 帮助中的 "属性属性" 主题。

##  <a name="getindexcount"></a>CDaoTableDef::GetIndexCount

调用此成员函数可获取表的索引数。

```
short GetIndexCount();
```

### <a name="return-value"></a>返回值

表的索引数。

### <a name="remarks"></a>备注

如果其值为0，则集合中不存在索引。

相关信息，请参阅 DAO 帮助中的 "计数属性" 主题。

##  <a name="getindexinfo"></a>CDaoTableDef：： GetIndexInfo

调用此成员函数可获取有关在 tabledef 中定义的索引的各种信息。

```
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
表的从零开始的索引集合中索引对象的数值索引，用于按其在集合中的位置进行查找。

*indexinfo*<br/>
对[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构的引用。

*dwInfoOptions*<br/>
用于指定要检索的索引信息的选项。 此处列出了可用的选项，以及它们导致函数返回的内容：

- `AFX_DAO_PRIMARY_INFO` 名称、字段信息、字段。 使用此选项以实现最高性能。

- `AFX_DAO_SECONDARY_INFO` 主要信息，外加： Primary、Unique、聚集、Ignore Null、Required、Foreign

- `AFX_DAO_ALL_INFO` 主要和辅助信息，以及：非重复计数

*lpszName*<br/>
一个指针，指向索引对象的名称，用于按名称进行查找。

### <a name="remarks"></a>备注

函数的一个版本可让你按索引在集合中的位置进行查找。 其他版本允许您按名称查找索引。

有关所返回信息的说明，请参阅[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构。 此结构中有与*dwInfoOptions*中的说明中列出的信息项对应的成员。 当你在一个级别请求信息时，还会获取任何以前的级别的信息。

有关相关信息，请参阅 DAO 帮助中的 "属性属性" 主题。

##  <a name="getname"></a>CDaoTableDef：： GetName

调用此成员函数以获取基础表的用户定义名称。

```
CString GetName();
```

### <a name="return-value"></a>返回值

用户为表定义的名称。

### <a name="remarks"></a>备注

此名称以字母开头，最多可包含64个字符。 它可以包含数字和下划线字符，但不能包含标点或空格。

有关相关信息，请参阅 DAO 帮助中的主题 "名称属性"。

##  <a name="getrecordcount"></a>CDaoTableDef：： GetRecordCount

调用此成员函数以了解 `CDaoTableDef` 对象中有多少条记录。

```
long GetRecordCount();
```

### <a name="return-value"></a>返回值

在 tabledef 对象中访问的记录数。

### <a name="remarks"></a>备注

为表类型 `CDaoTableDef` 对象调用 `GetRecordCount` 会反映表中记录的大致数量，并会在添加和删除表记录时立即受到影响。 在调用[CDaoWorkSpace：： CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase)之前，已回滚的事务将作为记录计数的一部分出现。 不包含记录的 `CDaoTableDef` 对象的 "记录计数" 属性设置为0。 使用附加表或 ODBC 数据库时，`GetRecordCount` 始终返回-1。

有关相关信息，请参阅 DAO 帮助中的主题 "RecordCount 属性"。

##  <a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName

调用此成员函数可在源数据库中检索附加表的名称。

```
CString GetSourceTableName();
```

### <a name="return-value"></a>返回值

一个 `CString` 对象，该对象指定附加表的源名称; 如果为，则为空字符串（如果为本机数据表）。

### <a name="remarks"></a>备注

附加表是链接到 Microsoft Jet 数据库的另一个数据库中的表。 附加表的数据保留在外部数据库中，其他应用程序可以在该数据库中对其进行操作。

有关相关信息，请参阅 DAO 帮助中的主题 "SourceTableName 属性"。

##  <a name="getvalidationrule"></a>CDaoTableDef::GetValidationRule

调用此成员函数来检索 tabledef 的验证规则。

```
CString GetValidationRule();
```

### <a name="return-value"></a>返回值

一个 `CString` 对象，它在字段更改或添加到表中时对其数据进行验证。

### <a name="remarks"></a>备注

验证规则与更新操作一起使用。 如果 tabledef 包含验证规则，则在更改数据之前，对 tabledef 的更新必须符合预先确定的条件。 如果更改与条件不匹配，则会引发包含[GetValidationText](#getvalidationtext)值的异常。 对于 `CDaoTableDef` 对象，此 `CString` 对于附加表是只读的，而对于基表是读/写的。

有关相关信息，请参阅 DAO 帮助中的主题 "有效性规则属性"。

##  <a name="getvalidationtext"></a>CDaoTableDef::GetValidationText

调用此函数可检索当用户输入与验证规则不匹配的数据时要显示的字符串。

```
CString GetValidationText();
```

### <a name="return-value"></a>返回值

一个 `CString` 对象，该对象指定在用户输入与验证规则不匹配的数据时所显示的文本。

### <a name="remarks"></a>备注

对于 `CDaoTableDef` 对象，此 `CString` 对于附加表是只读的，而对于基表是读/写的。

有关相关信息，请参阅 DAO 帮助中的主题 "有效性文本属性"。

##  <a name="isopen"></a>CDaoTableDef：： IsOpen

调用此成员函数以确定当前是否打开了 `CDaoTableDef` 对象。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果 `CDaoTableDef` 对象处于打开状态，则为非零值;否则为0。

### <a name="remarks"></a>备注

##  <a name="m_pdatabase"></a>CDaoTableDef：： m_pDatabase

包含指向此表的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象的指针。

### <a name="remarks"></a>备注

##  <a name="m_pdaotabledef"></a>CDaoTableDef：： m_pDAOTableDef

包含指向 `CDaoTableDef` 对象基础上的 DAO tabledef 对象的 OLE 接口的指针。

### <a name="remarks"></a>备注

如果需要直接访问 DAO 界面，请使用此指针。

##  <a name="open"></a>CDaoTableDef：： Open

调用此成员函数以打开以前保存在数据库的 TableDef's 集合中的 tabledef。

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
指向指定表名称的字符串的指针。

### <a name="remarks"></a>备注

##  <a name="refreshlink"></a>CDaoTableDef::RefreshLink

调用此成员函数以更新附加表的连接信息。

```
void RefreshLink();
```

### <a name="remarks"></a>备注

通过在相应的 `CDaoTableDef` 对象上调用[SetConnect](#setconnect) ，然后使用 `RefreshLink` 成员函数更新信息，可以更改附加表的连接信息。 在调用 `RefreshLink`时，附加表的属性将不会更改。

若要强制修改后的连接信息生效，则必须关闭基于此 tabledef 的所有打开的[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。

有关相关信息，请参阅 DAO 帮助中的 "RefreshLink 方法" 主题。

##  <a name="setattributes"></a>CDaoTableDef：： SetAttributes

设置一个值，该值指示 `CDaoTableDef` 对象的一个或多个特性。

```
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>参数

*lAttributes*<br/>
`CDaoTableDef` 对象所表示的表的特征，可以是以下常量的总和：

|常量|说明|
|--------------|-----------------|
|`dbAttachExclusive`|对于使用 Microsoft Jet 数据库引擎的数据库，指示表是一个打开以供独占使用的附加表。|
|`dbAttachSavePWD`|对于使用 Microsoft Jet 数据库引擎的数据库，指示附加表的用户 ID 和密码与连接信息一起保存。|
|`dbSystemObject`|指示表是由 Microsoft Jet 数据库引擎提供的系统表。|
|`dbHiddenObject`|指示表是由 Microsoft Jet 数据库引擎提供的隐藏表。|

### <a name="remarks"></a>备注

设置多个属性时，可以使用按位 "或" 运算符来对适当的常量求和。 为非附加表设置 `dbAttachExclusive` 将产生异常。 合并以下值还会产生异常：

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

有关相关信息，请参阅 DAO 帮助中的 "属性属性" 主题。

##  <a name="setconnect"></a>CDaoTableDef::SetConnect

对于表示附加表的 `CDaoTableDef` 对象，string 对象包含一个或两个部分（数据库类型说明符和数据库的路径）。

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>参数

*lpszConnect*<br/>
指向字符串表达式的指针，该字符串表达式指定要传递给 ODBC 或可安装的 ISAM 驱动程序的其他参数。

### <a name="remarks"></a>备注

下表中所示的路径是包含数据库文件的目录的完整路径，必须在其前面加上标识符 "DATABASE ="。 在某些情况下（与 Microsoft Jet 和 Microsoft Excel 数据库一样），数据库路径参数中包含特定的文件名。

> [!NOTE]
>  不要在 "DATABASE = drive：\\\path" 形式的等号路径语句周围加入空格。 这将导致引发异常并导致连接失败。

下表显示了可能的数据库类型及其相应的数据库说明符和路径：

|数据库类型|说明符|Path|
|-------------------|---------------|----------|
|使用 Jet 数据库引擎的数据库|"[`database`];"|"`drive`：\\\ *路径*\\\ *文件名*.MDB|
|dBASE III|"dBASE III;"|"`drive`：\\\ *路径*"|
|dBASE IV|"dBASE IV;"|"`drive`：\\\ *路径*"|
|dBASE 5|"dBASE 5.0;"|"`drive`：\\\ *路径*"|
|Paradox 1。x|"Paradox 1.x;"|"`drive`：\\\ *路径*"|
|Paradox 4。x|"Paradox 4.x;"|"`drive`：\\\ *路径*"|
|Paradox 6。x|"Paradox 5. x;"|"`drive`：\\\ *路径*"|
|Excel 3.0|"Excel 3.0;"|"`drive`：\\\ *路径*\\\ *文件名*。XLS|
|Excel 4.0|"Excel 4.0;"|"`drive`：\\\ *路径*\\\ *文件名*。XLS|
|Excel 5.0 或 Excel 95|"Excel 5.0;"|"`drive`：\\\ *路径*\\\ *文件名*。XLS|
|Excel 97|"Excel 8.0;"|"`drive`：\\\ *路径*\ *文件名*。XLS|
|HTML 导入|"HTML Import;"|"`drive`：\\\ *路径*\ *文件名*"|
|HTML 导出|"HTML Export;"|"`drive`：\\\ *路径*"|
|文本|"Text;"|"drive：\\\path"|
|ODBC|ODBCDATABASE = `database`;UID = *user*;PWD = *password*;DSN =*值 1;* LOGINTIMEOUT =*秒;* "（这可能不是所有服务器的完整连接字符串; 这只是一个示例。 参数之间不能有空格，这一点非常重要。）|无|
|Exchange|外汇<br /><br /> MAPILEVEL = *folderpath*;<br /><br /> [TABLETYPE={ 0 &#124; 1 };]<br /><br /> [PROFILE = *profile*;]<br /><br /> [PWD = *password*;]<br /><br /> [DATABASE = `database`;] "|*"驱动器*：\\\ *路径*\\\ *文件名*.MDB|

> [!NOTE]
>  在 DAO 3.5 中不再支持 Btrieve。

必须在连接字符串中使用双反斜杠（\\\\）。 如果已使用 `SetConnect`修改了现有连接的属性，则必须随后调用[RefreshLink](#refreshlink)。 如果使用 `SetConnect`初始化连接属性，则无需调用 `RefreshLink`，但如果选择这样做，请先追加 tabledef。

如果需要密码，但未提供，则在首次访问表时，ODBC 驱动程序将显示一个登录对话框，如果连接已关闭并重新打开，则为。

您可以通过向 `Create` 成员函数提供源参数来设置 `CDaoTableDef` 对象的连接字符串。 您可以通过检查设置来确定数据库的类型、路径、用户 ID、密码或 ODBC 数据源。 有关详细信息，请参阅特定驱动程序的文档。

相关信息，请参阅 DAO 帮助中的 "连接属性" 主题。

##  <a name="setname"></a>CDaoTableDef：： SetName

调用此成员函数可为表设置用户定义的名称。

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
一个指针，指向指定表名称的字符串表达式。

### <a name="remarks"></a>备注

名称必须以字母开头，并且最多可以包含64个字符。 它可以包含数字和下划线字符，但不能包含标点或空格。

有关相关信息，请参阅 DAO 帮助中的主题 "名称属性"。

##  <a name="setsourcetablename"></a>CDaoTableDef::SetSourceTableName

调用此成员函数以指定附加表的名称或 `CDaoTableDef` 对象所基于的基表的名称，因为它存在于数据的原始源中。

```
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>参数

*lpszSrcTableName*<br/>
一个指针，它指向指定外部数据库中的表名称的字符串表达式。 对于基表，此设置为空字符串（""）。

### <a name="remarks"></a>备注

然后，必须调用[RefreshLink](#refreshlink)。 对于某个附加表，此属性设置为空; 对于附加的表，此属性设置为空; 对于不追加到集合的对象，此属性设置为空。

有关相关信息，请参阅 DAO 帮助中的主题 "SourceTableName 属性"。

##  <a name="setvalidationrule"></a>CDaoTableDef::SetValidationRule

调用此成员函数可设置 tabledef 的验证规则。

```
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>参数

*lpszValidationRule*<br/>
一个指针，指向用于验证操作的字符串表达式。

### <a name="remarks"></a>备注

验证规则与更新操作一起使用。 如果 tabledef 包含验证规则，则在更改数据之前，对 tabledef 的更新必须符合预先确定的条件。 如果更改与条件不匹配，则会显示包含[GetValidationText](#getvalidationtext)文本的异常。

只有使用 Microsoft Jet 数据库引擎的数据库才支持验证。 表达式不能引用用户定义函数、域聚合函数、SQL 聚合函数或查询。 `CDaoTableDef` 对象的验证规则可以引用该对象中的多个字段。

例如，对于名为*hire_date*和*termination_date*的字段，验证规则可能是：

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

有关相关信息，请参阅 DAO 帮助中的主题 "有效性规则属性"。

##  <a name="setvalidationtext"></a>CDaoTableDef::SetValidationText

调用此成员函数可为具有 Microsoft Jet 数据库引擎支持的基础基表的 `CDaoTableDef` 对象设置验证规则的异常文本。

```
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>参数

*lpszValidationText*<br/>
一个指向字符串表达式的指针，该字符串表达式指定在输入的数据无效时所显示的文本。

### <a name="remarks"></a>备注

不能设置附加表的验证文本。

有关相关信息，请参阅 DAO 帮助中的主题 "有效性文本属性"。

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)
