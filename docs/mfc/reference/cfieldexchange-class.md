---
title: CFieldExchange 课程
ms.date: 11/04/2016
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
helpviewer_keywords:
- CFieldExchange [MFC], IsFieldType
- CFieldExchange [MFC], SetFieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
ms.openlocfilehash: d4b99a4992075072253d4f9b3182a926673bdfd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373933"
---
# <a name="cfieldexchange-class"></a>CFieldExchange 课程

支持数据库类使用的记录字段交换 (RFX) 和批量记录字段交换 (Bulk RFX) 例程。

## <a name="syntax"></a>语法

```
class CFieldExchange
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CFieldExchange：：场位类型](#isfieldtype)|如果当前操作适合更新的字段类型，则返回非零。|
|[CFieldExchange：setField类型](#setfieldtype)|指定记录集数据成员的类型 （ 列或参数 - 由以下所有对 RFX 函数的调用，`SetFieldType`直到下一次调用 。|

## <a name="remarks"></a>备注

`CFieldExchange`没有基类。

如果要为自定义数据类型编写数据交换例程，或者在实现批量行提取时，请使用此类;否则，您不会直接使用此类。 RFX 和批量 RFX 在记录集对象的字段数据成员和数据源上的当前记录的相应字段之间交换数据。

> [!NOTE]
> 如果您使用的是数据访问对象 （DAO） 类，而不是开放数据库连接 （ODBC） 类，请使用类[CDaoFieldExchange。](../../mfc/reference/cdaofieldexchange-class.md) 有关详细信息，请参阅文章[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)。

`CFieldExchange`对象提供进行记录字段交换或批量记录字段交换所需的上下文信息。 `CFieldExchange`对象支持许多操作，包括绑定参数和字段数据成员，以及在当前记录的字段上设置各种标志。 RFX 和批量 RFX 操作在 中定义的类型类型的记录集类数据成员**enum****上**`CFieldExchange`执行。 可能的**字段类型**值包括：

- `CFieldExchange::outputColumn`用于字段数据成员。

- `CFieldExchange::inputParam`或`CFieldExchange::param`用于输入参数数据成员。

- `CFieldExchange::outputParam`用于输出参数数据成员。

- `CFieldExchange::inoutParam`用于输入/输出参数数据成员。

类的大多数成员函数和数据成员都用于编写您自己的自定义 RFX 例程。 您将`SetFieldType`经常使用。 有关详细信息，请参阅[文章记录字段交换 （RFX）](../../data/odbc/record-field-exchange-rfx.md)和[记录集 （ODBC）。](../../data/odbc/recordset-odbc.md) 有关批量行提取的信息，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 有关 RFX 和批量 RFX 全局函数的详细信息，请参阅此参考的 MFC 宏和全局部分中的[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CFieldExchange`

## <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="cfieldexchangeisfieldtype"></a><a name="isfieldtype"></a>CFieldExchange：：场位类型

如果编写自己的 RFX 函数，请在`IsFieldType`函数的开头调用以确定是否可以对特定字段或参数`CFieldExchange::outputColumn`数据成员类型（a、 `CFieldExchange::inputParam` `CFieldExchange::param`、、、`CFieldExchange::outputParam`或`CFieldExchange::inoutParam`） 执行当前操作。

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>参数

*pnField*<br/>
在此参数中返回字段或参数数据成员的顺序数。 此数字对应于[CRecordset：:DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[CRecordset：:DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)函数中的数据成员的顺序。

### <a name="return-value"></a>返回值

如果可以在当前字段或参数类型上执行当前操作，则非零。

### <a name="remarks"></a>备注

遵循现有 RFX 函数的模型。

## <a name="cfieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CFieldExchange：setField类型

您需要`SetFieldType`在记录集类的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)覆盖中调用。

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>参数

*nFieldType*<br/>
中`enum FieldType``CFieldExchange`声明的值可以是以下值之一：

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>备注

对于现场数据成员，必须调用`SetFieldType`参数 ，`CFieldExchange::outputColumn`后跟对 RFX 或批量 RFX 函数的调用。 如果尚未实现批量行提取，则 ClassWizard 将此`SetFieldType`调用放在`DoFieldExchange`的字段映射部分中。

如果参数化记录集类，则必须在任何字段映射节`SetFieldType`之外再次调用，然后对所有参数数据成员进行 RFX 调用。 每种类型的参数数据成员必须有自己的`SetFieldType`调用。 下表区分了可以传递给`SetFieldType`以表示类的参数数据成员的不同值：

|设置字段类型参数值|参数数据成员的类型|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|输入参数。 传递到记录集的查询或存储过程的值。|
|`CFieldExchange::param` | 与`CFieldExchange::inputParam`相同。|
|`CFieldExchange::outputParam`|输出参数。 记录集存储过程的返回值。|
|`CFieldExchange::inoutParam`|输入/输出参数。 传入记录集的存储过程并从中返回的值。|

通常，与字段数据成员或参数数据成员关联的每组 RFX 函数调用之前都必须调用`SetFieldType`。 每个`SetFieldType`调用的`SetFieldType`*nFieldType*参数标识调用后 RFX 函数调用表示的数据成员的类型。

有关处理输出和输入/输出参数的详细信息，请参阅`CRecordset`成员函数[FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset)。 有关 RFX 和批量 RFX 函数的详细信息，请参阅主题[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。 有关批量行提取的相关信息，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

### <a name="example"></a>示例

此示例显示对 RFX 函数的多个调用以及对`SetFieldType`的附带调用。 请注意，`SetFieldType`通过`pFX`指向`CFieldExchange`对象的指针调用。

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)
