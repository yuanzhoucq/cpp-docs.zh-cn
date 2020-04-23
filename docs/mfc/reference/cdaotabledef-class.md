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
ms.openlocfilehash: adc31ccbf2be34aa1df1fa56111d1990701a6329
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754685"
---
# <a name="cdaotabledef-class"></a>CDaoTableDef 类

表示基表或附加表的已存储定义。

## <a name="syntax"></a>语法

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDaoTableDef：cdaoTableDef](#cdaotabledef)|构造 `CDaoTableDef` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDaoTableDef：：附加](#append)|向数据库添加新表。|
|[CDaoTableDef：可以更新](#canupdate)|如果可以更新表（您可以修改字段或表属性的定义），则返回非零。|
|[CDaoTableDef：关闭](#close)|关闭打开的表def。|
|[CDaoTableDef：创建](#create)|创建一个表，该表可以使用[附加程序](#append)添加到数据库中。|
|[CDaoTableDef：创建字段](#createfield)|调用以创建表的字段。|
|[CDaoTableDef：创建索引](#createindex)|调用以创建表的索引。|
|[CDaoTableDef：:DeleteField](#deletefield)|调用以从表中删除字段。|
|[CDaoTableDef：:DeleteIndex](#deleteindex)|调用以从表中删除索引。|
|[CDaoTableDef：获取属性](#getattributes)|返回指示`CDaoTableDef`对象的一个或多个特征的值。|
|[CDaoTableDef：获取连接](#getconnect)|返回提供有关表源的信息的值。|
|[CDaoTableDef：获取日期创建](#getdatecreated)|返回创建对象基础的基表的`CDaoTableDef`日期和时间。|
|[CDaoTableDef：获取更新日期](#getdatelastupdated)|返回对基表设计进行的最新更改的日期和时间。|
|[CDaoTableDef：获取字段计数](#getfieldcount)|返回表示表中的字段数的值。|
|[CDaoTableDef：获取菲尔德信息](#getfieldinfo)|返回有关表中字段的特定类型的信息。|
|[CDaoTableDef：获取索引计数](#getindexcount)|返回表的索引数。|
|[CDaoTableDef：获取索引信息](#getindexinfo)|返回有关表索引的特定类型的信息。|
|[CDaoTableDef：获取名称](#getname)|返回表的用户定义名称。|
|[CDaoTableDef：获取记录计数](#getrecordcount)|返回表中的记录数。|
|[CDaoTableDef：获取源表名称](#getsourcetablename)|返回指定源数据库中附加表名称的值。|
|[CDaoTableDef：获取验证规则](#getvalidationrule)|返回一个值，用于在字段中验证数据在更改或添加到表中时。|
|[CDaoTableDef：获取验证文本](#getvalidationtext)|返回一个值，该值指定如果 Field 对象的值不符合指定的验证规则，则应用程序显示的消息文本。|
|[CDaoTableDef：即开放](#isopen)|如果表处于打开状态，则返回非零。|
|[CDaoTableDef：：打开](#open)|打开存储在数据库的 TableDef 集合中的现有表def。|
|[CDaoTableDef：：刷新链接](#refreshlink)|更新附加表的连接信息。|
|[CDaoTableDef：设置属性](#setattributes)|设置指示`CDaoTableDef`对象的一个或多个特征的值。|
|[CDaoTableDef：set连接](#setconnect)|设置提供有关表源的信息的值。|
|[CDaoTableDef：set 名称](#setname)|设置表的名称。|
|[CDaoTableDef：：设置源表名称](#setsourcetablename)|设置指定源数据库中附加表名称的值。|
|[CDaoTableDef：设置验证规则](#setvalidationrule)|设置一个值，在字段中的数据被更改或添加到表中时对其进行验证。|
|[CDaoTableDef：set验证文本](#setvalidationtext)|设置一个值，用于指定如果 Field 对象的值不符合指定的验证规则，则应用程序显示的消息文本。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CDaoTableDef：m_pDAOTableDef](#m_pdaotabledef)|指向 tabledef 对象基础的 DAO 接口的指针。|
|[CDaoTableDef：m_pDatabase](#m_pdatabase)|此表的源数据库。|

## <a name="remarks"></a>备注

每个 DAO 数据库对象维护一个集合，称为 TableDefs，其中包含所有保存的 DAO 表def对象。

使用`CDaoTableDef`对象操作表定义。 例如，你能够：

- 检查数据库中任何本地表、附加表或外部表的字段和索引结构。

- 调用`SetConnect`附加`SetSourceTableName`表 和 成员函数，并使用`RefreshLink`成员函数更新到附加表的连接。

- 调用`CanUpdate`成员函数以确定是否可以编辑表中的字段定义。

- 使用`GetValidationRule`和`SetValidationRule`和 和`GetValidationText``SetValidationText`成员函数获取或设置验证条件。

- 使用`Open`成员函数创建表、动态集或快照类型`CDaoRecordset`对象。

    > [!NOTE]
    >  DAO 数据库类不同于基于开放数据库连接 （ODBC） 的 MFC 数据库类。 所有 DAO 数据库类名称都有"CDao"前缀。 您仍可以使用 DAO 类访问 ODBC 数据源;DAO 类通常提供卓越的功能，因为它们特定于 Microsoft Jet 数据库引擎。

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>使用 tabledef 对象处理现有表或创建新表

1. 在所有情况下，首先构造一个`CDaoTableDef`对象，提供指向表所属的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象的指针。

1. 然后执行以下操作，具体取决于所需内容：

   - 要使用现有的已保存表，请调用 tabledef 对象的[Open](#open)成员函数，提供已保存表的名称。

   - 要创建新表，请调用 tabledef 对象的["创建](#create)成员"函数，提供表的名称。 调用[CreateField](#createfield)和[CreateIndex](#createindex)将字段和索引添加到表中。

   - 调用[附加程序](#append)，通过将表追加到数据库的 TableDefs 集合来保存表。 `Create`将表def置于打开状态，因此在调用`Create`后不调用`Open`。

        > [!TIP]
        >  创建保存的表的最简单方法是创建它们并使用 Microsoft Access 将它们存储在数据库中。 然后，您可以在 MFC 代码中打开并使用它们。

要使用已打开或创建的表def对象，请创建并打开`CDaoRecordset`对象，在`dbOpenTable`*nOpenType*参数中指定具有值的表def的名称。

要使用 tabledef 对象创建`CDaoRecordset`对象，通常创建或打开如上所述的表def，然后构造记录集对象，在调用[CDaoRecordset：：：打开](../../mfc/reference/cdaorecordset-class.md#open)时将指针传递给表def对象。 传递的表def必须处于打开状态。 有关详细信息，请参阅类[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

使用 tabledef 对象完成后，调用其[Close](../../mfc/reference/cdaorecordset-class.md#close)成员函数;如果使用表def 对象，则调用其 Close 成员函数。然后销毁表def对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="cdaotabledefappend"></a><a name="append"></a>CDaoTableDef：：附加

调用[Create](#create)后调用此成员函数以创建新的表def对象以将表def保存在数据库中。

```
virtual void Append();
```

### <a name="remarks"></a>备注

函数将对象追加到数据库的 TableDefs 集合中。 在定义 tabledef 时，可以通过不追加表定义表def，但如果要保存和使用表def，则必须调用`Append`。

> [!NOTE]
> 如果尝试追加未命名的表def（包含空字符串或空字符串），MFC 将引发异常。

有关相关信息，请参阅 DAO 帮助中的主题"附加方法"。

## <a name="cdaotabledefcanupdate"></a><a name="canupdate"></a>CDaoTableDef：可以更新

调用此成员函数以确定是否可以更改`CDaoTableDef`对象基础表的定义。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>返回值

如果可以修改表结构（架构）（模式）（添加或删除字段和索引），则非零，否则为 0。

### <a name="remarks"></a>备注

默认情况下，可以更新对象基础的新`CDaoTableDef`创建的表，并且无法更新对象基础的附加`CDaoTableDef`表。 对象`CDaoTableDef`可能是可向上的，即使生成的记录集不可升。

有关相关信息，请参阅 DAO 帮助中的主题"可使用属性"。

## <a name="cdaotabledefcdaotabledef"></a><a name="cdaotabledef"></a>CDaoTableDef：cdaoTableDef

构造 `CDaoTableDef` 对象。

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>参数

*p数据库*<br/>
指向[CDao 数据库](../../mfc/reference/cdaodatabase-class.md)对象的指针。

### <a name="remarks"></a>备注

构造对象后，必须调用["创建](#create)"或["打开](#open)"成员函数。 完成该对象后，必须调用其[Close](#close)成员函数并销毁该`CDaoTableDef`对象。

## <a name="cdaotabledefclose"></a><a name="close"></a>CDaoTableDef：关闭

调用此成员函数以关闭和释放表def对象。

```
virtual void Close();
```

### <a name="remarks"></a>备注

通常在调用`Close`后，如果表def对象是使用**new**分配的，则删除该对象。

调用 后可以再次调用`Close`[Open。](#open) 这允许您重用表def对象。

有关相关信息，请参阅 DAO 帮助中的主题"关闭方法"。

## <a name="cdaotabledefcreate"></a><a name="create"></a>CDaoTableDef：创建

调用此成员函数以创建新的保存表。

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
指向包含表名称的字符串的指针。

*l 属性*<br/>
对应于表def对象表示的表特征的值。 您可以使用位-OR 组合以下任一常量：

|返回的常量|说明|
|--------------|-----------------|
|`dbAttachExclusive`|对于使用 Microsoft Jet 数据库引擎的数据库，指示该表是打开供独占用途的附加表。|
|`dbAttachSavePWD`|对于使用 Microsoft Jet 数据库引擎的数据库，指示附加表的用户 ID 和密码与连接信息一起保存。|
|`dbSystemObject`|指示该表是 Microsoft Jet 数据库引擎提供的系统表。|
|`dbHiddenObject`|指示该表是 Microsoft Jet 数据库引擎提供的隐藏表。|

*lpszSrcTable*<br/>
指向包含源表名称的字符串的指针。 默认情况下，此值初始化为 NULL。

*lpszConnect*<br/>
指向包含默认连接字符串的字符串的指针。 默认情况下，此值初始化为 NULL。

### <a name="remarks"></a>备注

命名表def后，可以调用[Append](#append)将表def保存在数据库的 TableDefs 集合中。 调用`Append`后，tabledef 处于打开状态，您可以使用它创建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象。

有关相关信息，请参阅 DAO 帮助中的主题"创建TableDef 方法"。

## <a name="cdaotabledefcreatefield"></a><a name="createfield"></a>CDaoTableDef：创建字段

调用此成员函数以向表添加字段。

```cpp
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
指向指定此字段名称的字符串表达式的指针。

nType**<br/>
指示字段数据类型的值。 该设置可以是以下值之一：

|类型|大小（字节）|说明|
|----------|--------------------|-----------------|
|`dbBoolean`|1 字节|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|货币 （ [COle 货币](../../mfc/reference/colecurrency-class.md)）|
|`dbSingle`|4|FLOAT|
|`dbDouble`|8|double|
|`dbDate`|8|日期/时间 （ [COleDatetime](../../atl-mfc-shared/reference/coledatetime-class.md)）|
|`dbText`|1 - 255|文本 （ [CString](../../atl-mfc-shared/reference/cstringt-class.md)）|
|`dbLongBinary`|0|长二进制 （OLE 对象[）、CLongBinary](../../mfc/reference/clongbinary-class.md)或[CBytearray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|备忘录 （ [CString](../../atl-mfc-shared/reference/cstringt-class.md)）|

*lSize*<br/>
指示包含文本或包含文本或数值的字段的最大大小（以字节为单位）的值。 除了文本字段外，所有字段都忽略*lSize*参数。

*l 属性*<br/>
与字段的特征对应的值，可以使用位-OR 进行组合。

|返回的常量|说明|
|--------------|-----------------|
|`dbFixedField`|字段大小是固定的（数字字段的默认值）。|
|`dbVariableField`|字段大小是可变的（仅限文本字段）。|
|`dbAutoIncrField`|新记录的字段值将自动递增为无法更改的唯一长整数。 仅支持 Microsoft Jet 数据库表。|
|`dbUpdatableField`|可以更改字段值。|
|`dbDescending`|该字段按降序（Z - A 或 100 - 0）顺序排序（仅适用于 Index 对象的字段集合中的字段对象）。 如果省略此常量，则字段按升序（A - Z 或 0 - 100）顺序排序（默认值）。|

*菲尔德信息*<br/>
对[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构的引用。

### <a name="remarks"></a>备注

将`DAOField`创建 （OLE） 对象并将其追加到 （OLE）`DAOTableDef`对象的字段集合中。 除了用于检查对象属性外，您还可以使用`CDaoFieldInfo`构造输入参数以在 tabledef 中创建新字段。 的第`CreateField`一个版本更易于使用，但如果要进行更精细的控制，可以使用`CreateField`的第二个版本，该版本需要一个`CDaoFieldInfo`参数。

如果使用该参数的版本`CreateField`，`CDaoFieldInfo`则必须仔细设置`CDaoFieldInfo`结构的每个以下成员：

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

其余成员`CDaoFieldInfo`应设置为**0**、FALSE 或空字符串（适用于成员）或`CDaoException`可能发生。

有关相关信息，请参阅 DAO 帮助中的主题"创建字段方法"。

## <a name="cdaotabledefcreateindex"></a><a name="createindex"></a>CDaoTableDef：创建索引

调用此函数以向表添加索引。

```cpp
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>参数

*索引信息*<br/>
对[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构的引用。

### <a name="remarks"></a>备注

索引指定从数据库表访问的记录的顺序，以及是否接受重复记录。 索引还提供对数据的有效访问。

您不必为表创建索引，但在大型未编制索引的表中，访问特定记录或创建记录集可能需要很长时间。 另一方面，创建过多的索引会降低更新、追加和删除操作的速度，因为所有索引都会自动更新。 在决定要创建哪些索引时，请考虑这些因素。

必须设置结构的`CDaoIndexInfo`以下成员：

- `m_strName`必须提供名称。

- `m_pFieldInfos`必须指向结构数组`CDaoIndexFieldInfo`。

- `m_nFields`必须指定结构数组中的字段数`CDaoFieldInfo`。

如果设置为 FALSE，将忽略其余成员。 此外，在`m_lDistinctCount`创建索引期间将忽略该成员。

## <a name="cdaotabledefdeletefield"></a><a name="deletefield"></a>CDaoTableDef：:DeleteField

调用此成员函数以删除字段并使它无法访问。

```cpp
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
指向字符串表达式的指针，该指针表达式是现有字段的名称。

*nIndex*<br/>
表的零基字段集合中的字段索引，用于按索引查找。

### <a name="remarks"></a>备注

您可以在尚未追加到数据库的新对象上或[CanUpdate](#canupdate)返回非零时使用此成员函数。

有关相关信息，请参阅 DAO 帮助中的主题"删除方法"。

## <a name="cdaotabledefdeleteindex"></a><a name="deleteindex"></a>CDaoTableDef：:DeleteIndex

调用此成员函数以删除基础表中的索引。

```cpp
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
指向字符串表达式的指针，该指针表达式是现有索引的名称。

*nIndex*<br/>
数据库的零基表Defs集合中索引对象的数组索引，用于按索引查找。

### <a name="remarks"></a>备注

您可以在尚未追加到数据库的新对象上或[CanUpdate](#canupdate)返回非零时使用此成员函数。

有关相关信息，请参阅 DAO 帮助中的主题"删除方法"。

## <a name="cdaotabledefgetattributes"></a><a name="getattributes"></a>CDaoTableDef：获取属性

对于`CDaoTableDef`对象，返回值指定由对象表示的`CDaoTableDef`表的特征，并且可以是这些常量的总和：

```
long GetAttributes();
```

### <a name="return-value"></a>返回值

返回指示`CDaoTableDef`对象的一个或多个特征的值。

### <a name="remarks"></a>备注

|返回的常量|说明|
|--------------|-----------------|
|`dbAttachExclusive`|对于使用 Microsoft Jet 数据库引擎的数据库，指示该表是打开供独占用途的附加表。|
|`dbAttachSavePWD`|对于使用 Microsoft Jet 数据库引擎的数据库，指示附加表的用户 ID 和密码与连接信息一起保存。|
|`dbSystemObject`|指示该表是 Microsoft Jet 数据库引擎提供的系统表。|
|`dbHiddenObject`|指示该表是 Microsoft Jet 数据库引擎提供的隐藏表。|
|`dbAttachedTable`|指示表是来自非 ODBC 数据库（如 Paradox 数据库）的附加表。|
|`dbAttachedODBC`|指示表是来自 ODBC 数据库（如 Microsoft SQL Server）的附加表。|

系统表是 Microsoft Jet 数据库引擎创建的包含各种内部信息的表。

隐藏表是为 Microsoft Jet 数据库引擎临时使用而创建的表。

有关相关信息，请参阅 DAO 帮助中的主题"属性属性"。

## <a name="cdaotabledefgetconnect"></a><a name="getconnect"></a>CDaoTableDef：获取连接

调用此成员函数以获取数据源的连接字符串。

```
CString GetConnect();
```

### <a name="return-value"></a>返回值

包含`CString`表的路径和数据库类型的对象。

### <a name="remarks"></a>备注

对于表示`CDaoTableDef`附加表的对象，`CString`该对象由一个或两个部分（数据库类型指定器和数据库路径）组成。

下表所示的路径是包含数据库文件的目录的完整路径，前面必须前面有标识符"DATABASE_"。 在某些情况下（与 Microsoft Jet 和 Microsoft Excel 数据库一样），数据库路径参数中包含特定的文件名。

[CDaoTableDef：setConnect](#setconnect)中的表显示可能的数据库类型及其相应的数据库指定和路径：

对于 Microsoft Jet 数据库基表，指定器是一个空字符串 （""）。

如果需要密码但未提供密码，ODBC 驱动程序会在首次访问表时显示一个登录对话框;如果连接已关闭并重新打开，则再次显示登录对话框。 如果附加的表具有该`dbAttachSavePWD`属性，则重新打开表时不会显示登录提示。

有关相关信息，请参阅 DAO 帮助中的主题"连接属性"。

## <a name="cdaotabledefgetdatecreated"></a><a name="getdatecreated"></a>CDaoTableDef：获取日期创建

调用此函数以确定创建对象基础的表的`CDaoTableDef`日期和时间。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>返回值

包含创建对象基础`CDaoTableDef`表的日期和时间的值。

### <a name="remarks"></a>备注

日期和时间设置派生自创建或上次更新基表的计算机。 在多用户环境中，用户应直接从文件服务器获取这些设置，以避免差异;也就是说，所有客户端都应使用"标准"时间源 - 可能来自一台服务器。

有关相关信息，请参阅 DAO 帮助中的主题"创建日期，上次更新的属性"。

## <a name="cdaotabledefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoTableDef：获取更新日期

调用此函数以确定上次更新对象基础的表的`CDaoTableDef`日期和时间。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>返回值

包含上次更新对象基础表的`CDaoTableDef`日期和时间的值。

### <a name="remarks"></a>备注

日期和时间设置派生自创建或上次更新基表的计算机。 在多用户环境中，用户应直接从文件服务器获取这些设置，以避免差异;也就是说，所有客户端都应使用"标准"时间源 - 可能来自一台服务器。

有关相关信息，请参阅 DAO 帮助中的主题"创建日期，上次更新的属性"。

## <a name="cdaotabledefgetfieldcount"></a><a name="getfieldcount"></a>CDaoTableDef：获取字段计数

调用此成员函数以检索表中定义的字段数。

```
short GetFieldCount();
```

### <a name="return-value"></a>返回值

表中的字段数。

### <a name="remarks"></a>备注

如果其值为 0，则集合中没有对象。

有关相关信息，请参阅 DAO 帮助中的主题"计数属性"。

## <a name="cdaotabledefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoTableDef：获取菲尔德信息

调用此成员函数以获取有关表def中定义的字段的各种信息。

```cpp
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
表的零基字段集合中字段对象的索引，用于按索引查找。

*菲尔德信息*<br/>
对[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构的引用。

*dwInfoOptions*<br/>
指定要检索的字段的信息的选项。 此处列出了可用的选项以及它们导致函数返回的内容：

- `AFX_DAO_PRIMARY_INFO`（默认）名称、类型、大小、属性。 使用此选项可获得最快的性能。

- `AFX_DAO_SECONDARY_INFO`主要信息，加上：序号位置、必需位置、允许零长度、分词顺序、外名、源字段、源表

- `AFX_DAO_ALL_INFO`主要和辅助信息，以及：验证规则、验证文本、默认值

*lpsz名称*<br/>
指向字段对象名称的指针，用于按名称查找。 该名称是一个字符串，最多 64 个字符，用于唯一命名字段。

### <a name="remarks"></a>备注

函数的一个版本允许您按索引查找字段。 另一个版本允许您按名称查找字段。

有关返回的信息的说明，请参阅[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 此结构的成员对应于*dwInfoOptions*描述中列出的信息项。 当您在一个级别请求信息时，您也获取任何先前级别的信息。

有关相关信息，请参阅 DAO 帮助中的主题"属性属性"。

## <a name="cdaotabledefgetindexcount"></a><a name="getindexcount"></a>CDaoTableDef：获取索引计数

调用此成员函数以获取表的索引数。

```
short GetIndexCount();
```

### <a name="return-value"></a>返回值

表的索引数。

### <a name="remarks"></a>备注

如果其值为 0，则集合中没有索引。

有关相关信息，请参阅 DAO 帮助中的主题"计数属性"。

## <a name="cdaotabledefgetindexinfo"></a><a name="getindexinfo"></a>CDaoTableDef：获取索引信息

调用此成员函数以获取有关表def中定义的索引的各种信息。

```cpp
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
表中的零基索引集合中索引对象的数字索引，用于按其在集合中的位置进行查找。

*索引信息*<br/>
对[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构的引用。

*dwInfoOptions*<br/>
指定要检索的索引的信息的选项。 此处列出了可用的选项以及它们导致函数返回的内容：

- `AFX_DAO_PRIMARY_INFO`名称，字段信息，字段。 使用此选项可获得最快的性能。

- `AFX_DAO_SECONDARY_INFO`主要信息，加上：主信息、唯一信息、群集、忽略空值、必需信息、外信息

- `AFX_DAO_ALL_INFO`主要和次要信息，加上：不同的计数

*lpsz名称*<br/>
指向索引对象名称的指针，用于按名称查找。

### <a name="remarks"></a>备注

函数的一个版本允许您按索引在集合中的位置查找索引。 另一个版本允许您按名称查找索引。

有关返回的信息的说明，请参阅[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构。 此结构的成员对应于*dwInfoOptions*描述中列出的信息项。 当您在一个级别请求信息时，您也获取任何先前级别的信息。

有关相关信息，请参阅 DAO 帮助中的主题"属性属性"。

## <a name="cdaotabledefgetname"></a><a name="getname"></a>CDaoTableDef：获取名称

调用此成员函数以获取基础表的用户定义名称。

```
CString GetName();
```

### <a name="return-value"></a>返回值

表的用户定义名称。

### <a name="remarks"></a>备注

此名称以字母开头，最多可包含 64 个字符。 它可以包括数字和下划线字符，但不能包括标点符号或空格。

有关相关信息，请参阅 DAO 帮助中的主题"名称属性"。

## <a name="cdaotabledefgetrecordcount"></a><a name="getrecordcount"></a>CDaoTableDef：获取记录计数

调用此成员函数以了解`CDaoTableDef`对象中有多少条记录。

```
long GetRecordCount();
```

### <a name="return-value"></a>返回值

在 tabledef 对象中访问的记录数。

### <a name="remarks"></a>备注

调用`GetRecordCount`表类型`CDaoTableDef`对象反映表中记录的近似数量，并且随着表记录的添加和删除而立即受到影响。 回滚的事务将作为记录计数的一部分出现，直到您调用[CDaoWorkSpace：：压缩数据库](../../mfc/reference/cdaoworkspace-class.md#compactdatabase)。 没有`CDaoTableDef`记录的对象的记录计数属性设置为 0。 使用附加的表或 ODBC 数据库`GetRecordCount`时，始终返回 -1。

有关相关信息，请参阅 DAO 帮助中的主题"记录计数属性"。

## <a name="cdaotabledefgetsourcetablename"></a><a name="getsourcetablename"></a>CDaoTableDef：获取源表名称

调用此成员函数以检索源数据库中附加表的名称。

```
CString GetSourceTableName();
```

### <a name="return-value"></a>返回值

指定`CString`附加表的源名称的对象，或指定本机数据表的空字符串。

### <a name="remarks"></a>备注

附加的表是另一个数据库中链接到 Microsoft Jet 数据库的表。 附加表的数据将保留在外部数据库中，可以由其他应用程序对其进行操作。

有关相关信息，请参阅 DAO 帮助中的主题"源表名称属性"。

## <a name="cdaotabledefgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoTableDef：获取验证规则

调用此成员函数以检索表def的验证规则。

```
CString GetValidationRule();
```

### <a name="return-value"></a>返回值

在`CString`字段中更改数据或添加到表中时验证数据的对象。

### <a name="remarks"></a>备注

验证规则用于与更新操作有关。 如果 tabledef 包含验证规则，则对该表def 的更新必须在更改数据之前匹配预定的条件。 如果更改与条件不匹配，则会引发包含[Get验证文本](#getvalidationtext)值的异常。 对于`CDaoTableDef`对象，这是`CString`附加表的只读表和基表的读/写。

有关相关信息，请参阅 DAO 帮助中的主题"验证规则属性"。

## <a name="cdaotabledefgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoTableDef：获取验证文本

调用此函数以检索在用户输入与验证规则不匹配的数据时显示的字符串。

```
CString GetValidationText();
```

### <a name="return-value"></a>返回值

指定`CString`用户输入的数据与验证规则不匹配时显示的文本的对象。

### <a name="remarks"></a>备注

对于`CDaoTableDef`对象，这是`CString`附加表的只读表和基表的读/写。

有关相关信息，请参阅 DAO 帮助中的主题"验证文本属性"。

## <a name="cdaotabledefisopen"></a><a name="isopen"></a>CDaoTableDef：即开放

调用此成员函数以确定`CDaoTableDef`对象当前是否打开。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果对象处于打开`CDaoTableDef`状态，则非零;否则 0。

### <a name="remarks"></a>备注

## <a name="cdaotabledefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoTableDef：m_pDatabase

包含指向此表的[CDao 数据库](../../mfc/reference/cdaodatabase-class.md)对象的指针。

### <a name="remarks"></a>备注

## <a name="cdaotabledefm_pdaotabledef"></a><a name="m_pdaotabledef"></a>CDaoTableDef：m_pDAOTableDef

包含指向对象基础的 DAO 表def对象的 OLE 接口的`CDaoTableDef`指针。

### <a name="remarks"></a>备注

如果需要直接访问 DAO 接口，请使用此指针。

## <a name="cdaotabledefopen"></a><a name="open"></a>CDaoTableDef：：打开

调用此成员函数以打开以前保存在数据库的 TableDef 集合中的表def。

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
指向指定表名称的字符串的指针。

### <a name="remarks"></a>备注

## <a name="cdaotabledefrefreshlink"></a><a name="refreshlink"></a>CDaoTableDef：：刷新链接

调用此成员函数以更新附加表的连接信息。

```cpp
void RefreshLink();
```

### <a name="remarks"></a>备注

通过在相应`CDaoTableDef`对象上调用[SetConnect，](#setconnect)然后使用成员函数更新信息，`RefreshLink`可以更改附加表的连接信息。 调用`RefreshLink`时，不会更改附加表的属性。

要强制修改后的连接信息生效，必须关闭基于此表def的所有打开[的 CDaoRecordset 对象](../../mfc/reference/cdaorecordset-class.md)。

有关相关信息，请参阅 DAO 帮助中的主题"刷新链接方法"。

## <a name="cdaotabledefsetattributes"></a><a name="setattributes"></a>CDaoTableDef：设置属性

设置指示`CDaoTableDef`对象的一个或多个特征的值。

```cpp
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>参数

*l 属性*<br/>
由`CDaoTableDef`对象表示的表的特征，可以是这些常量的总和：

|返回的常量|说明|
|--------------|-----------------|
|`dbAttachExclusive`|对于使用 Microsoft Jet 数据库引擎的数据库，指示该表是打开供独占用途的附加表。|
|`dbAttachSavePWD`|对于使用 Microsoft Jet 数据库引擎的数据库，指示附加表的用户 ID 和密码与连接信息一起保存。|
|`dbSystemObject`|指示该表是 Microsoft Jet 数据库引擎提供的系统表。|
|`dbHiddenObject`|指示该表是 Microsoft Jet 数据库引擎提供的隐藏表。|

### <a name="remarks"></a>备注

设置多个属性时，可以使用位-OR 运算符求和适当的常量来组合它们。 在`dbAttachExclusive`未连接的表上设置会产生异常。 组合以下值也会产生异常：

- **dbAttach 独家&#124; dbattachODBC**

- **dbAttachsavePWD&#124; dbattach表**

有关相关信息，请参阅 DAO 帮助中的主题"属性属性"。

## <a name="cdaotabledefsetconnect"></a><a name="setconnect"></a>CDaoTableDef：set连接

对于表示`CDaoTableDef`附加表的对象，字符串对象由一个或两个部分组成（数据库类型指定器和数据库路径）。

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>参数

*lpszConnect*<br/>
指向字符串表达式的指针，用于指定要传递给 ODBC 或可安装 ISAM 驱动程序的其他参数。

### <a name="remarks"></a>备注

下表所示的路径是包含数据库文件的目录的完整路径，前面必须前面有标识符"DATABASE_"。 在某些情况下（与 Microsoft Jet 和 Microsoft Excel 数据库一样），数据库路径参数中包含特定的文件名。

> [!NOTE]
> 请勿在窗体"DATABASE_驱动器：_path"\\的等号登录路径语句周围包含空格。 这将导致引发异常和连接失败。

下表显示了可能的数据库类型及其相应的数据库指定器和路径：

|数据库类型|说明符|路径|
|-------------------|---------------|----------|
|使用 Jet 数据库引擎的数据库|"[ `database`];"|`drive`\ *filename**path*： 路径\\文件名 。\\\ MDB"|
|dBASE III|"dBASE III;"|" `drive`\\\ ：*路径*"|
|dBASE IV|"dBASE IV;"|" `drive`\\\ ：*路径*"|
|dBASE 5|"dBASE 5.0;"|" `drive`\\\ ：*路径*"|
|悖论 3.x|"悖论 3.x;"|" `drive`\\\ ：*路径*"|
|悖论 4.x|"悖论 4.x;"|" `drive`\\\ ：*路径*"|
|悖论 5.x|"悖论 5.x;"|" `drive`\\\ ：*路径*"|
|Excel 3.0|"Excel 3.0;"|`drive`\ *filename**path*： 路径\\文件名 。\\\ XLS"|
|Excel 4.0|"Excel 4.0;"|`drive`\ *filename**path*： 路径\\文件名 。\\\ XLS"|
|Excel 5.0 或 Excel 95|"Excel 5.0;"|`drive`\ *filename**path*： 路径\\文件名 。\\\ XLS"|
|Excel 97|"Excel 8.0;"|\ \ *filename**path*： `drive`路径文件名\\。XLS"|
|HTML 导入|"HTML 导入;"|： `drive`\\\ *path*路径\ *文件名*"|
|HTML 导出|"HTML 导出;"|" `drive`\\\ ：*路径*"|
|文本|"文本;"|"驱动器：\path"\\|
|ODBC|"ODBC;数据库* `database`;UID+*用户*;PWD=*密码*;DSN=*数据源名称;* 登录时间+*秒数;*"（这可能不是所有服务器的完整连接字符串;它只是一个示例。 参数之间不要有空格是非常重要的。|无|
|Exchange|"交换;<br /><br /> MAPILEVEL=*文件夹路径*;<br /><br /> [表类型] 0 &#124; 1 {;}<br /><br /> [*配置文件;]*<br /><br /> [PWD]*密码*;]<br /><br /> [数据库];" `database`|*"驱动器*\\\ *路径*\\\ *文件名*。MDB"|

> [!NOTE]
> 从 DAO 3.5 起，Btrieve 不再受支持。

必须在连接字符串中使用双反斜杠\\\\（ ） 。 如果已使用`SetConnect`修改了现有连接的属性，则必须随后调用[RefreshLink](#refreshlink)。 如果使用 初始化连接属性`SetConnect`，则不需要调用`RefreshLink`，但如果选择这样做，请先追加表def。

如果需要密码但未提供密码，ODBC 驱动程序会在首次访问表时显示一个登录对话框;如果连接已关闭并重新打开，则再次显示登录对话框。

可以通过向`Create`成员函数提供源参数来`CDaoTableDef`设置对象的连接字符串。 您可以检查该设置以确定数据库的类型、路径、用户 ID、密码或 ODBC 数据源。 有关详细信息，请参阅特定驱动程序的文档。

有关相关信息，请参阅 DAO 帮助中的主题"连接属性"。

## <a name="cdaotabledefsetname"></a><a name="setname"></a>CDaoTableDef：set 名称

调用此成员函数以设置表的用户定义的名称。

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
指向指定表名称的字符串表达式的指针。

### <a name="remarks"></a>备注

名称必须以字母开头，最多包含 64 个字符。 它可以包括数字和下划线字符，但不能包括标点符号或空格。

有关相关信息，请参阅 DAO 帮助中的主题"名称属性"。

## <a name="cdaotabledefsetsourcetablename"></a><a name="setsourcetablename"></a>CDaoTableDef：：设置源表名称

调用此成员函数以指定附加表的名称或`CDaoTableDef`对象所基于的基表的名称，因为它存在于数据的原始源中。

```cpp
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>参数

*lpszSrcTable名称*<br/>
指向在外部数据库中指定表名称的字符串表达式的指针。 对于基表，该设置为空字符串 （"）。

### <a name="remarks"></a>备注

然后，您必须调用[刷新链接](#refreshlink)。 此属性设置对于基表为空，对于附加的表或未追加到集合的对象，则读/写。

有关相关信息，请参阅 DAO 帮助中的主题"源表名称属性"。

## <a name="cdaotabledefsetvalidationrule"></a><a name="setvalidationrule"></a>CDaoTableDef：设置验证规则

调用此成员函数以设置表def的验证规则。

```cpp
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>参数

*lpsz验证规则*<br/>
指向验证操作的字符串表达式的指针。

### <a name="remarks"></a>备注

验证规则用于与更新操作有关。 如果 tabledef 包含验证规则，则对该表def 的更新必须在更改数据之前匹配预定的条件。 如果更改与条件不匹配，将显示包含[Get验证文本文本](#getvalidationtext)的异常。

仅支持使用 Microsoft Jet 数据库引擎的数据库验证。 表达式不能引用用户定义的函数、域聚合函数、SQL 聚合函数或查询。 `CDaoTableDef`对象的验证规则可以引用该对象的多个字段。

例如，对于名为*hire_date*和*termination_date*的字段，验证规则可能是：

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

有关相关信息，请参阅 DAO 帮助中的主题"验证规则属性"。

## <a name="cdaotabledefsetvalidationtext"></a><a name="setvalidationtext"></a>CDaoTableDef：set验证文本

调用此成员函数为具有 Microsoft Jet 数据库引擎支持的基础`CDaoTableDef`基表的对象设置验证规则的异常文本。

```cpp
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>参数

*lpsz验证文本*<br/>
指向字符串表达式的指针，用于指定如果输入的数据无效时显示的文本。

### <a name="remarks"></a>备注

不能设置附加表的验证文本。

有关相关信息，请参阅 DAO 帮助中的主题"验证文本属性"。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDao记录组类](../../mfc/reference/cdaorecordset-class.md)
