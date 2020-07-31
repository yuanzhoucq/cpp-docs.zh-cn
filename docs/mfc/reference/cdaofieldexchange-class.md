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
ms.openlocfilehash: 62e9d1917e2d1eea19b9e8db4b6c56b6ad25d9e9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231827"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange 类

支持 DAO 数据库类使用的 DAO 记录字段交换 (DFX) 例程。

DAO 受 Office 2013 的支持。 DAO 3.6 是最终版本，被视为已过时。

## <a name="syntax"></a>语法

```
class CDaoFieldExchange
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CDaoFieldExchange：： IsValidOperation](#isvalidoperation)|如果当前操作适合要更新的字段类型，则返回非零值。|
|[CDaoFieldExchange：： SetFieldType](#setfieldtype)|指定记录集数据成员的类型（列或参数），由对 DFX 函数的所有后续调用表示，直到下一次调用 `SetFieldType` 。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CDaoFieldExchange：： m_nOperation](#m_noperation)|由当前对记录集的成员函数的调用执行的 DFX 操作 `DoFieldExchange` 。|
|[CDaoFieldExchange：： m_prs](#m_prs)|指向正在执行 DFX 操作的记录集的指针。|

## <a name="remarks"></a>备注

`CDaoFieldExchange`没有基类。

如果要为自定义数据类型编写数据交换例程，请使用此类;否则，你将不会直接使用此类。 DFX 在[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象的字段数据成员与数据源中的当前记录的对应字段之间交换数据。 DFX 从数据源和数据源管理两个方向的交换。 有关编写自定义 DFX 例程的信息，请参阅[技术说明 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) 。

> [!NOTE]
> DAO 数据库类与基于开放式数据库连接（ODBC）的 MFC 数据库类不同。 所有 DAO 数据库类名称都具有 "CDao" 前缀。 你仍可以使用 DAO 类访问 ODBC 数据源。 通常，基于 DAO 的 MFC 类比基于 ODBC 的 MFC 类更强大。 基于 DAO 的类可以通过其自己的数据库引擎来访问数据，包括通过 ODBC 驱动程序。 它们还支持数据定义语言（DDL）操作，例如通过类添加表，而无需自行调用 DAO。

> [!NOTE]
> DAO 记录字段交换（DFX）与基于 ODBC 的 MFC 数据库类（，）中的记录字段交换（RFX）非常 `CDatabase` 相似 `CRecordset` 。 如果你了解 RFX，则可以轻松使用 DFX。

`CDaoFieldExchange`对象提供要进行 DAO 记录字段交换所需的上下文信息。 `CDaoFieldExchange`对象支持许多操作，包括绑定参数和字段数据成员以及在当前记录的字段上设置各种标志。 DFX 操作对中由 FieldType 定义的类型的记录集类数据成员执行 **`enum`** **FieldType** `CDaoFieldExchange` 。 可能的**FieldType**值包括：

- `CDaoFieldExchange::outputColumn`对于字段数据成员。

- `CDaoFieldExchange::param`对于参数数据成员。

提供[IsValidOperation](#isvalidoperation)成员函数来编写您自己的自定义 DFX 例程。 你将在 CDaoRecordset 中频繁使用[SetFieldType](#setfieldtype) [：:D ofieldexchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)函数。 有关 DFX 全局函数的详细信息，请参阅[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。 有关为你自己的数据类型编写自定义 DFX 例程的信息，请参阅[技术说明 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CDaoFieldExchange`

## <a name="requirements"></a>要求

**标头：** afxdao

## <a name="cdaofieldexchangeisvalidoperation"></a><a name="isvalidoperation"></a>CDaoFieldExchange：： IsValidOperation

如果你编写自己的 DFX 函数，请 `IsValidOperation` 在函数的开始处调用，以确定是否可以在特定字段数据成员类型（或）上执行当前操作 `CDaoFieldExchange::outputColumn` `CDaoFieldExchange::param` 。

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>返回值

如果当前操作适合要更新的字段类型，则为非零值。

### <a name="remarks"></a>备注

DFX 机制执行的某些操作仅适用于其中一种可能的字段类型。 遵循现有 DFX 函数的模型。

有关编写自定义 DFX 例程的其他信息，请参阅[技术说明 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。

## <a name="cdaofieldexchangem_noperation"></a><a name="m_noperation"></a>CDaoFieldExchange：： m_nOperation

标识要对与字段交换对象相关联的[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象执行的操作。

### <a name="remarks"></a>备注

`CDaoFieldExchange`对象为记录集的多个不同 DFX 操作提供上下文。

> [!NOTE]
> 以下 MarkForAddNew 和 SetFieldNull 操作下描述的 PSEUDONULL 值是用于将字段标记为 Null 的值。 DAO 记录字段交换机制（DFX）使用此值来确定哪些字段已显式标记为 Null。 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)和[COleCurrency](../../mfc/reference/colecurrency-class.md)字段不需要 PSEUDONULL。

的可能值 `m_nOperation` 为：

|Operation|说明|
|---------------|-----------------|
|`AddToParameterList`|生成 SQL 语句的**参数**子句。|
|`AddToSelectList`|生成 SQL 语句的**SELECT**子句。|
|`BindField`|将数据库中的字段绑定到应用程序中的内存位置。|
|`BindParam`|为记录集的查询设置参数值。|
|`Fixup`|为字段设置 Null 状态。|
|`AllocCache`|分配用于检查记录集中 "更新" 字段的缓存。|
|`StoreField`|将当前记录保存到缓存中。|
|`LoadField`|还原记录集中的缓存数据成员变量。|
|`FreeCache`|释放用于检查记录集中 "更新" 字段的缓存。|
|`SetFieldNull`|将字段的状态设置为 Null，并将值设置为 PSEUDONULL。|
|`MarkForAddNew`|如果不 PSEUDONULL，则将字段标记为 "脏"。|
|`MarkForEdit`|如果字段 "更新" 与缓存不匹配，则将其标记为 "脏"。|
|`SetDirtyField`|将标记为 "已更新" 的字段值设置为。|
|`DumpField`|转储字段的内容（仅限调试）。|
|`MaxDFXOperation`|用于输入检查。|

## <a name="cdaofieldexchangem_prs"></a><a name="m_prs"></a>CDaoFieldExchange：： m_prs

包含指向与对象关联的[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象的指针 `CDaoFieldExchange` 。

### <a name="remarks"></a>备注

## <a name="cdaofieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CDaoFieldExchange：： SetFieldType

`SetFieldType`在 `CDaoRecordset` 类的 `DoFieldExchange` 重写中调用。

```cpp
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>参数

*nFieldType*<br/>
在中声明的**枚举 FieldType**的值 `CDaoFieldExchange` ，可以是下列值之一：

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>备注

通常，ClassWizard 会为你编写此调用。 如果你编写自己的函数，并使用向导编写 `DoFieldExchange` 函数，则在字段映射外添加对你自己的函数的调用。 如果不使用该向导，则将不会有字段映射。 调用先调用 DFX 函数，对类的每个字段数据成员分别调用，并将字段类型标识为 `CDaoFieldExchange::outputColumn` 。

如果对记录集类进行参数化，则应为所有参数数据成员（在字段映射外）添加 DFX 调用，并在调用之前调用 `SetFieldType` 。 传递值 `CDaoFieldExchange::param` 。 （您可以改为使用[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)并设置其参数值。）

通常，与字段数据成员或参数数据成员关联的每组 DFX 函数调用都必须在调用之前进行 `SetFieldType` 。 每个调用的*nFieldType*参数 `SetFieldType` 标识按调用后的 DFX 函数调用所表示的数据成员的类型 `SetFieldType` 。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)
