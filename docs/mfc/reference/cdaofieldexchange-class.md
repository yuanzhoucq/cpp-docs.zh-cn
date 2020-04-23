---
title: CDaoFieldExchange 类
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
ms.openlocfilehash: 86f12f78338d1c60e3dd13614ccedc2868f28d81
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754716"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange 类

支持 DAO 数据库类使用的 DAO 记录字段交换 (DFX) 例程。

通过 Office 2013 支持 DAO。 DAO 3.6 是最终版本，它被视为过时版本。

## <a name="syntax"></a>语法

```
class CDaoFieldExchange
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDao现场交易：有效操作](#isvalidoperation)|如果当前操作适合更新的字段类型，则返回非零。|
|[CDao现场交换：：集场类型](#setfieldtype)|指定记录集数据成员的类型 （ 列或参数 - 由对 DFX 函数的所有后续调用，直到`SetFieldType`下一次调用 DFX 函数为止。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CDao现场交易：m_nOperation](#m_noperation)|当前对记录集成员函数的调用正在执行的`DoFieldExchange`DFX 操作。|
|[CDao现场交易：m_prs](#m_prs)|指向正在对其中执行 DFX 操作的记录集的指针。|

## <a name="remarks"></a>备注

`CDaoFieldExchange`没有基类。

如果要为自定义数据类型编写数据交换例程，请使用此类;否则，您不会直接使用此类。 DFX 在[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象的字段数据成员和数据源上的当前记录的相应字段之间交换数据。 DFX 从数据源到数据源，双向管理交换。 有关编写自定义 DFX 例程的信息[，请参阅技术说明 53。](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)

> [!NOTE]
> DAO 数据库类不同于基于开放数据库连接 （ODBC） 的 MFC 数据库类。 所有 DAO 数据库类名称都有"CDao"前缀。 您仍可以使用 DAO 类访问 ODBC 数据源。 通常，基于 DAO 的 MFC 类比基于 ODBC 的 MFC 类更有能力。 基于 DAO 的类可以通过自己的数据库引擎访问数据，包括通过 ODBC 驱动程序。 它们还支持数据定义语言 （DDL） 操作，例如通过类添加表，而不必自己调用 DAO。

> [!NOTE]
> DAO 记录字段交换 （DFX） 与基于 ODBC 的 MFC 数据库类 （）`CDatabase`中的记录字段`CRecordset`交换 （RFX） 非常相似。 如果您了解 RFX，您会发现使用 DFX 很容易。

`CDaoFieldExchange`对象提供进行 DAO 记录字段交换所需的上下文信息。 `CDaoFieldExchange`对象支持许多操作，包括绑定参数和字段数据成员，以及在当前记录的字段上设置各种标志。 DFX 操作在 中定义的**类型**类型的记录集类数据**成员上**`CDaoFieldExchange`执行。 可能的**字段类型**值包括：

- `CDaoFieldExchange::outputColumn`用于字段数据成员。

- `CDaoFieldExchange::param`用于参数数据成员。

[IsValid操作](#isvalidoperation)成员函数用于编写您自己的自定义 DFX 例程。 您将在[CDaoRecordset：:DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)功能中经常使用[SetFieldType。](#setfieldtype) 有关 DFX 全局函数的详细信息，请参阅[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。 有关为您自己的数据类型编写自定义 DFX 例程的信息，请参阅[技术说明 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CDaoFieldExchange`

## <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="cdaofieldexchangeisvalidoperation"></a><a name="isvalidoperation"></a>CDao现场交易：有效操作

如果编写自己的 DFX 函数，请在`IsValidOperation`函数的开头调用以确定是否可以对特定字段数据成员类型 （a`CDaoFieldExchange::outputColumn`或 a `CDaoFieldExchange::param`） 执行当前操作。

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>返回值

如果当前操作适合更新的字段类型，则非零。

### <a name="remarks"></a>备注

DFX 机制执行的某些操作仅适用于可能字段类型之一。 遵循现有 DFX 函数的模型。

有关编写自定义 DFX 例程的其他信息，请参阅[技术说明 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。

## <a name="cdaofieldexchangem_noperation"></a><a name="m_noperation"></a>CDao现场交易：m_nOperation

标识要在与字段交换对象关联的[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象上执行的操作。

### <a name="remarks"></a>备注

该`CDaoFieldExchange`对象为记录集中的许多不同的 DFX 操作提供上下文。

> [!NOTE]
> 下面的 MarkForAddNew 和 SetFieldNull 操作下描述的 PSEUDONULL 值是用于标记字段 Null 的值。 DAO 记录字段交换机制 （DFX） 使用此值来确定已显式标记为 Null 的字段。 [COleDateTime 和](../../atl-mfc-shared/reference/coledatetime-class.md) [COle 货币](../../mfc/reference/colecurrency-class.md)字段不需要 PSEUDONULL。

的可能`m_nOperation`值为：

|Operation|说明|
|---------------|-----------------|
|`AddToParameterList`|生成 SQL 语句的**PARAMETERS**子句。|
|`AddToSelectList`|生成 SQL 语句的**SELECT**子句。|
|`BindField`|将数据库中的字段绑定到应用程序中的内存位置。|
|`BindParam`|为记录集的查询设置参数值。|
|`Fixup`|设置字段的 Null 状态。|
|`AllocCache`|分配用于检查记录集中的"脏"字段的缓存。|
|`StoreField`|将当前记录保存到缓存中。|
|`LoadField`|还原记录集中的缓存数据成员变量。|
|`FreeCache`|释放用于检查记录集中的"脏"字段的缓存。|
|`SetFieldNull`|将字段的状态设置为"空"，并将值设置为 PSEUDONULL。|
|`MarkForAddNew`|标记为字段"脏"，如果不是 PSEUDONULL。|
|`MarkForEdit`|如果字段与缓存不匹配，则标记它们"脏"。|
|`SetDirtyField`|设置标记为"脏"的字段值。|
|`DumpField`|转储字段的内容（仅限调试）。|
|`MaxDFXOperation`|用于输入检查。|

## <a name="cdaofieldexchangem_prs"></a><a name="m_prs"></a>CDao现场交易：m_prs

包含指向与`CDaoFieldExchange`该对象关联的[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象的指针。

### <a name="remarks"></a>备注

## <a name="cdaofieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CDao现场交换：：集场类型

在`SetFieldType``CDaoRecordset`类的`DoFieldExchange`重写中调用。

```cpp
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>参数

*nFieldType*<br/>
**枚举字段类型**的值 ，在 中`CDaoFieldExchange`声明，可以是以下任一值：

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>备注

通常，ClassWizard 会为您编写此呼叫。 如果您编写自己的函数并使用向导编写函数`DoFieldExchange`，请在字段映射之外向自己的函数添加调用。 如果不使用向导，则没有字段映射。 调用之前对 DFX 函数的调用（针对类的每个字段数据成员一个），并将字段类型标识为`CDaoFieldExchange::outputColumn`。

如果对记录集类进行参数化，则应为所有参数数据成员（字段映射外部）添加 DFX 调用，并在调用 的这些调用之前添加`SetFieldType`DFX 调用。 传递值`CDaoFieldExchange::param`。 （您可以改用[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)并设置其参数值。

通常，与字段数据成员或参数数据成员关联的每组 DFX 函数调用之前都必须对`SetFieldType`调用。 每个`SetFieldType`调用的`SetFieldType`*nFieldType*参数标识调用后 DFX 函数调用表示的数据成员的类型。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDao记录组类](../../mfc/reference/cdaorecordset-class.md)
