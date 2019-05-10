---
title: CDaoFieldExchange 类
ms.date: 11/04/2016
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
ms.openlocfilehash: d28739ced9aedd29106937cb717c87a241993036
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399795"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange 类

支持 DAO 数据库类使用的 DAO 记录字段交换 (DFX) 例程。

## <a name="syntax"></a>语法

```
class CDaoFieldExchange
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|返回非零，当前操作是否适合于所更新字段的类型。|
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|指定记录集数据成员的类型-列或参数，直到下一步调用由 DFX 函数对所有后续调用`SetFieldType`。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CDaoFieldExchange::m_nOperation](#m_noperation)|正在执行的当前调用到记录集的 DFX 操作`DoFieldExchange`成员函数。|
|[CDaoFieldExchange::m_prs](#m_prs)|指向要对其使用 DFX 进行操作的记录集的指针。|

## <a name="remarks"></a>备注

`CDaoFieldExchange` 没有基类。

如果要为自定义数据类型; 编写数据交换例程，请使用此类否则，你将直接使用此类。 DFX 之间交换数据的字段数据成员的你[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象和数据源上的当前记录的相应字段。 DFX 管理中两个方向的交换，从数据源和数据源。 请参阅[技术注意 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)有关编写自定义 DFX 例程信息。

> [!NOTE]
>  DAO 数据库类是不同于基于开放式数据库连接 (ODBC) 的 MFC 数据库类。 所有 DAO 数据库类名称都具有"CDao"前缀。 您仍然可以访问 ODBC 数据源对于 DAO 类。 一般情况下，基于 DAO 的 MFC 类是比基于 ODBC 的 MFC 类功能更强大。 基于 DAO 的类可以访问数据，包括通过 ODBC 驱动程序，通过其自己的数据库引擎。 它们还支持数据定义语言 (DDL) 操作，如添加表通过而无需自行调用 DAO 类。

> [!NOTE]
>  DAO 记录字段交换 (DFX) 是非常类似于基于 ODBC 的 MFC 数据库类中的记录字段交换 (RFX) ( `CDatabase`， `CRecordset`)。 如果您了解 RFX，你会发现易于使用 DFX。

一个`CDaoFieldExchange`对象提供的上下文信息所需的 DAO 记录字段交换发生。 `CDaoFieldExchange` 对象支持操作，包括绑定参数和字段数据成员和当前记录的字段上设置各种标志的数。 记录集类的定义的类型的数据成员执行 DFX 操作**enum** **FieldType**中`CDaoFieldExchange`。 可能**FieldType**的值为：

- `CDaoFieldExchange::outputColumn` 适用于字段数据成员。

- `CDaoFieldExchange::param` 适用于参数的数据成员。

[IsValidOperation](#isvalidoperation)成员函数提供有关编写你自己的自定义 DFX 例程。 将使用[SetFieldType](#setfieldtype)中经常你[CDaoRecordset::DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)函数。 有关 DFX 全局函数的详细信息，请参阅[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。 有关为你自己的数据类型编写自定义 DFX 例程的信息，请参阅[技术注意 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CDaoFieldExchange`

## <a name="requirements"></a>要求

**标头：** afxdao.h

##  <a name="isvalidoperation"></a>  CDaoFieldExchange::IsValidOperation

如果您编写您自己 DFX 函数，请调用`IsValidOperation`函数来确定是否可以针对特定字段数据成员类型执行当前操作的开始处 (`CDaoFieldExchange::outputColumn`或`CDaoFieldExchange::param`)。

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>返回值

如果当前操作适用于所更新字段的类型，非零值。

### <a name="remarks"></a>备注

某些 DFX 机制所执行的操作仅适用于一种可能的字段类型。 遵循现有的 DFX 函数的模型。

有关编写自定义 DFX 例程的其他信息，请参阅[技术注意 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。

##  <a name="m_noperation"></a>  CDaoFieldExchange::m_nOperation

标识要执行的操作[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与字段 exchange 对象相关联的对象。

### <a name="remarks"></a>备注

`CDaoFieldExchange`对象提供对大量的不同记录集的 DFX 操作上下文。

> [!NOTE]
>  下面的 MarkForAddNew SetFieldNull 操作下所述的 PSEUDONULL 值是用来标记字段为 Null 的值。 DAO 记录字段交换机制 (DFX) 使用此值来确定哪些字段已显式标记为 Null。 不需要 PSEUDONULL [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)并[COleCurrency](../../mfc/reference/colecurrency-class.md)字段。

可能的值的`m_nOperation`是：

|操作|描述|
|---------------|-----------------|
|`AddToParameterList`|生成**参数**SQL 语句的子句。|
|`AddToSelectList`|生成**选择**SQL 语句的子句。|
|`BindField`|将数据库中的字段绑定到你的应用程序中的内存位置。|
|`BindParam`|设置记录集的查询参数的值。|
|`Fixup`|设置字段的 Null 状态。|
|`AllocCache`|分配用于检查"更新"中的字段记录集的缓存。|
|`StoreField`|将当前记录保存到缓存。|
|`LoadField`|还原在记录集的缓存的数据成员变量。|
|`FreeCache`|释放用于检查"更新"中的字段记录集的缓存。|
|`SetFieldNull`|字段的状态设置为 Null 和 PSEUDONULL 值。|
|`MarkForAddNew`|标记的字段"更新"如果不 PSEUDONULL。|
|`MarkForEdit`|如果它们不匹配缓存，标记字段"脏"。|
|`SetDirtyField`|设置字段值标记为"脏"。|
|`DumpField`|转储字段的内容 （仅限调试）。|
|`MaxDFXOperation`|用于输入检查。|

##  <a name="m_prs"></a>  CDaoFieldExchange::m_prs

包含一个指向[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与关联的对象`CDaoFieldExchange`对象。

### <a name="remarks"></a>备注

##  <a name="setfieldtype"></a>  CDaoFieldExchange::SetFieldType

调用`SetFieldType`在您`CDaoRecordset`类的`DoFieldExchange`重写。

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>参数

*nFieldType*<br/>
值为**枚举 FieldType**中声明`CDaoFieldExchange`，可以是以下之一：

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>备注

通常情况下，类向导为您编写此调用。 如果您编写自己的函数，并使用向导来编写在`DoFieldExchange`函数中，添加对外部字段映射函数的调用。 如果不使用该向导，未将字段映射。 在调用之前对 DFX 函数，一个用于您的类，每个字段数据成员的调用，并标识形式的字段类型`CDaoFieldExchange::outputColumn`。

如果参数化记录集类，应添加 DFX 调用 （映射外的字段） 的所有参数的数据成员和之前通过调用这些调用`SetFieldType`。 将值传递`CDaoFieldExchange::param`。 (相反，可以使用[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)并设置其参数的值。)

一般情况下，必须通过调用前面 DFX 函数调用与字段数据成员或参数数据成员关联的每个组`SetFieldType`。 *NFieldType*参数的每个`SetFieldType`调用标识按照 DFX 函数调用所表示的数据成员的类型`SetFieldType`调用。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)
