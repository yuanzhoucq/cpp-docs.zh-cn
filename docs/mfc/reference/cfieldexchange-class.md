---
title: CFieldExchange 类
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
ms.openlocfilehash: e66b3ed16d4f21d46567c37bfaf7929d32f63b8e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425897"
---
# <a name="cfieldexchange-class"></a>CFieldExchange 类

支持数据库类使用的记录字段交换 (RFX) 和批量记录字段交换 (Bulk RFX) 例程。

## <a name="syntax"></a>语法

```
class CFieldExchange
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CFieldExchange::IsFieldType](#isfieldtype)|如果当前操作适合要更新的字段类型，则返回非零值。|
|[CFieldExchange::SetFieldType](#setfieldtype)|指定记录集数据成员的类型（列或参数），由对 RFX 函数的所有以下调用表示，直到下一次调用 `SetFieldType`。|

## <a name="remarks"></a>备注

`CFieldExchange` 没有基类。

如果要为自定义数据类型编写数据交换例程，或在实现批量取行时使用此类，则为;否则，你将不会直接使用此类。 RFX 和批量 RFX 在记录集对象的字段数据成员与数据源中的当前记录的对应字段之间交换数据。

> [!NOTE]
>  如果使用的是数据访问对象（DAO）类而不是开放式数据库连接（ODBC）类，请改用类[CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) 。 有关详细信息，请参阅文章[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)。

`CFieldExchange` 对象提供记录字段交换或大容量记录字段交换所需的上下文信息。 `CFieldExchange` 对象支持多个操作，包括绑定参数和字段数据成员以及在当前记录的字段上设置各种标志。 RFX 和批量 RFX 操作在 `CFieldExchange`中由**枚举** **FieldType**定义的类型的记录集类数据成员上执行。 可能的**FieldType**值包括：

- 字段数据成员的 `CFieldExchange::outputColumn`。

- 输入参数数据成员的 `CFieldExchange::inputParam` 或 `CFieldExchange::param`。

- 输出参数数据成员的 `CFieldExchange::outputParam`。

- 输入/输出参数数据成员的 `CFieldExchange::inoutParam`。

该类的大多数成员函数和数据成员都是为编写您自己的自定义 RFX 例程而提供的。 你将频繁使用 `SetFieldType`。 有关详细信息，请参阅[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)和[记录集（ODBC）](../../data/odbc/recordset-odbc.md)一文。 有关批量行提取的信息，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。 有关 RFX 和批量 RFX 全局函数的详细信息，请参阅此引用的 MFC 宏和全局函数部分中的[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CFieldExchange`

## <a name="requirements"></a>要求

**标头：** afxdb

##  <a name="isfieldtype"></a>CFieldExchange::IsFieldType

如果你编写自己的 RFX 函数，请调用函数开头的 `IsFieldType`，以确定是否可以对特定字段或参数数据成员类型（`CFieldExchange::outputColumn`、`CFieldExchange::inputParam`、`CFieldExchange::param`、`CFieldExchange::outputParam`或 `CFieldExchange::inoutParam`）执行当前操作。

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>parameters

*pnField*<br/>
此参数中返回字段或参数数据成员的顺序号。 此数字对应于[CRecordset：:D ofieldexchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[CRecordset：:D obulkfieldexchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)函数中数据成员的顺序。

### <a name="return-value"></a>返回值

如果可以对当前字段或参数类型执行当前操作，则为非零值。

### <a name="remarks"></a>备注

遵循现有 RFX 函数的模型。

##  <a name="setfieldtype"></a>CFieldExchange::SetFieldType

你需要在记录集类的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)替代中调用 `SetFieldType`。

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>parameters

*nFieldType*<br/>
在 `CFieldExchange`中声明的 `enum FieldType`的值，可以是下列值之一：

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>备注

对于字段数据成员，必须使用 `CFieldExchange::outputColumn`的参数调用 `SetFieldType`，然后调用 RFX 或 Bulk RFX 函数。 如果尚未实现批量行提取，则 ClassWizard 会在 `DoFieldExchange`的 "字段映射" 部分中为您 `SetFieldType`。

如果参数化记录集类，则必须在任何字段映射节之外再次调用 `SetFieldType`，后跟对所有参数数据成员的 RFX 调用。 每种类型的参数数据成员都必须具有其自己的 `SetFieldType` 调用。 下表将可传递给 `SetFieldType` 的不同值区分为类的参数数据成员：

|SetFieldType 参数值|参数数据成员的类型|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|输入参数。 传递给记录集的查询或存储过程的值。|
|`CFieldExchange::param` | 与 `CFieldExchange::inputParam`相同。|
|`CFieldExchange::outputParam`|输出参数。 记录集的存储过程的返回值。|
|`CFieldExchange::inoutParam`|输入/输出参数。 传入并从记录集的存储过程返回的值。|

通常，与字段数据成员或参数数据成员关联的每个 RFX 函数调用都必须在调用 `SetFieldType`之前。 每个 `SetFieldType` 调用的*nFieldType*参数将标识按 `SetFieldType` 调用之后 RFX 函数调用所表示的数据成员的类型。

有关处理输出和输入/输出参数的详细信息，请参阅 `CRecordset` 成员函数[FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset)。 有关 RFX 和批量 RFX 函数的详细信息，请参阅主题[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。 有关批量行提取的相关信息，请参阅[记录记录：批量获取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>示例

此示例演示了对 `SetFieldType`的伴随调用调用 RFX 函数的多个调用。 请注意，通过指向 `CFieldExchange` 对象的 `pFX` 指针调用 `SetFieldType`。

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)
