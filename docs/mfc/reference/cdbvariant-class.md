---
title: CDBVariant 类
ms.date: 11/04/2016
f1_keywords:
- CDBVariant
- AFXDB/CDBVariant
- AFXDB/CDBVariant::CDBVariant
- AFXDB/CDBVariant::Clear
- AFXDB/CDBVariant::m_dwType
- AFXDB/CDBVariant::m_boolVal
- AFXDB/CDBVariant::m_chVal
- AFXDB/CDBVariant::m_dblVal
- AFXDB/CDBVariant::m_fltVal
- AFXDB/CDBVariant::m_iVal
- AFXDB/CDBVariant::m_lVal
- AFXDB/CDBVariant::m_pbinary
- AFXDB/CDBVariant::m_pdate
- AFXDB/CDBVariant::m_pstring
- AFXDB/CDBVariant::m_pstringA
- AFXDB/CDBVariant::m_pstringW
helpviewer_keywords:
- CDBVariant [MFC], CDBVariant
- CDBVariant [MFC], Clear
- CDBVariant [MFC], m_dwType
- CDBVariant [MFC], m_boolVal
- CDBVariant [MFC], m_chVal
- CDBVariant [MFC], m_dblVal
- CDBVariant [MFC], m_fltVal
- CDBVariant [MFC], m_iVal
- CDBVariant [MFC], m_lVal
- CDBVariant [MFC], m_pbinary
- CDBVariant [MFC], m_pdate
- CDBVariant [MFC], m_pstring
- CDBVariant [MFC], m_pstringA
- CDBVariant [MFC], m_pstringW
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
ms.openlocfilehash: 45a478a5ca6cfb4d9b976a29eae2ae7d98fdd6ee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223078"
---
# <a name="cdbvariant-class"></a>CDBVariant 类

表示 MFC ODBC 类的变量数据类型。

## <a name="syntax"></a>语法

```
class CDBVariant
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDBVariant：： CDBVariant](#cdbvariant)|构造 `CDBVariant` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CDBVariant：： Clear](#clear)|清除 `CDBVariant` 对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CDBVariant：： m_dwType](#m_dwtype)|包含当前存储的值的数据类型。 键入 `DWORD`。|

### <a name="public-union-members"></a>公共联合成员

|名称|说明|
|----------|-----------------|
|[CDBVariant：： m_boolVal](#m_boolval)|包含**BOOL**类型的值。|
|[CDBVariant：： m_chVal](#m_chval)|包含类型的值 **`unsigned char`** 。|
|[CDBVariant：： m_dblVal](#m_dblval)|包含类型的值 **`double`** 。|
|[CDBVariant：： m_fltVal](#m_fltval)|包含类型的值 **`float`** 。|
|[CDBVariant：： m_iVal](#m_ival)|包含类型的值 **`short`** 。|
|[CDBVariant：： m_lVal](#m_lval)|包含类型的值 **`long`** 。|
|[CDBVariant：： m_pbinary](#m_pbinary)|包含指向类型的对象的指针 `CLongBinary` 。|
|[CDBVariant：： m_pdate](#m_pdate)|包含指向**TIMESTAMP_STRUCT**类型的对象的指针。|
|[CDBVariant：： m_pstring](#m_pstring)|包含指向类型的对象的指针 `CString` 。|
|[CDBVariant：： m_pstringA](#m_pstringa)|存储指向 ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的指针。|
|[CDBVariant：： m_pstringW](#m_pstringw)|存储指向宽[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的指针。|

## <a name="remarks"></a>备注

`CDBVariant`没有基类。

`CDBVariant`类似于[COleVariant](../../mfc/reference/colevariant-class.md);但不 `CDBVariant` 使用 OLE。 `CDBVariant`允许您存储一个值，而无需担心值的数据类型。 `CDBVariant`跟踪存储在联合中的当前值的数据类型。

类[CRecordset](../../mfc/reference/crecordset-class.md)使用 `CDBVariant` 三个成员函数中的对象： `GetFieldValue` 、 `GetBookmark` 和 `SetBookmark` 。 例如， `GetFieldValue` 允许您动态提取列中的数据。 由于列的数据类型在运行时可能未知，因此 `GetFieldValue` 使用 `CDBVariant` 对象存储列的数据。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CDBVariant`

## <a name="requirements"></a>要求

**标头：** afxdb

## <a name="cdbvariantcdbvariant"></a><a name="cdbvariant"></a>CDBVariant：： CDBVariant

创建 NULL `CDBVariant` 对象。

```
CDBVariant();
```

### <a name="remarks"></a>备注

将[m_dwType](#m_dwtype)数据成员设置为 DBVT_NULL。

## <a name="cdbvariantclear"></a><a name="clear"></a>CDBVariant：： Clear

调用此成员函数以清除 `CDBVariant` 对象。

```cpp
void Clear();
```

### <a name="remarks"></a>备注

如果[m_dwType](#m_dwtype)数据成员的值是 DBVT_DATE、DBVT_STRING 或 DBVT_BINARY，则 `Clear` 释放与联合指针成员关联的内存。 `Clear`设置 `m_dwType` 为 DBVT_NULL。

`CDBVariant`析构函数调用 `Clear` 。

## <a name="cdbvariantm_boolval"></a><a name="m_boolval"></a>CDBVariant：： m_boolVal

存储类型为 BOOL 的值。

### <a name="remarks"></a>备注

`m_boolVal`数据成员属于联合。 在访问之前 `m_boolVal` ，请先检查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 设置为 DBVT_BOOL，则 `m_boolVal` 将包含有效的值; 否则，访问 `m_boolVal` 将产生不可靠的结果。

## <a name="cdbvariantm_chval"></a><a name="m_chval"></a>CDBVariant：： m_chVal

存储类型为的值 **`unsigned char`** 。

### <a name="remarks"></a>备注

`m_chVal`数据成员属于联合。 在访问之前 `m_chVal` ，请先检查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 设置为 DBVT_UCHAR，则 `m_chVal` 包含有效的值; 否则，访问 `m_chVal` 将产生不可靠的结果。

## <a name="cdbvariantm_dblval"></a><a name="m_dblval"></a>CDBVariant：： m_dblVal

存储类型为的值 **`double`** 。

### <a name="remarks"></a>备注

`m_dblVal`数据成员属于联合。 在访问之前 `m_dblVal` ，请先检查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 设置为 DBVT_DOUBLE，则 `m_dblVal` 包含有效的值; 否则，访问 `m_dblVal` 将产生不可靠的结果。

## <a name="cdbvariantm_dwtype"></a><a name="m_dwtype"></a>CDBVariant：： m_dwType

此数据成员包含当前存储在 `CDBVariant` 对象的联合数据成员中的值的数据类型。

### <a name="remarks"></a>备注

在访问此联合之前，必须检查的值才能 `m_dwType` 确定要访问的联合数据成员。 下表列出了的可能值 `m_dwType` ，以及相应的联合数据成员。

|m_dwType|联合数据成员|
|---------------|-----------------------|
|DBVT_NULL|没有可用于访问的联合成员。|
|DBVT_BOOL|[m_boolVal](#m_boolval)|
|DBVT_UCHAR|[m_chVal](#m_chval)|
|DBVT_SHORT|[m_iVal](#m_ival)|
|DBVT_LONG|[m_lVal](#m_lval)|
|DBVT_SINGLE|[m_fltVal](#m_fltval)|
|DBVT_DOUBLE|[m_dblVal](#m_dblval)|
|DBVT_DATE|[m_pdate](#m_pdate)|
|DBVT_STRING|[m_pstring](#m_pstring)|
|DBVT_BINARY|[m_pbinary](#m_pbinary)|
|DBVT_ASTRING|[m_pstringA](#m_pstringa)|
|DBVT_WSTRING|[m_pstringW](#m_pstringw)|

## <a name="cdbvariantm_fltval"></a><a name="m_fltval"></a>CDBVariant：： m_fltVal

存储类型为的值 **`float`** 。

### <a name="remarks"></a>备注

`m_fltVal`数据成员属于联合。 在访问之前 `m_fltVal` ，请先检查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 设置为 DBVT_SINGLE，则 `m_fltVal` 包含有效的值; 否则，访问 `m_fltVal` 将产生不可靠的结果。

## <a name="cdbvariantm_ival"></a><a name="m_ival"></a>CDBVariant：： m_iVal

存储类型为的值 **`short`** 。

### <a name="remarks"></a>备注

`m_iVal`数据成员属于联合。 在访问之前 `m_iVal` ，请先检查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 设置为 DBVT_SHORT，则 `m_iVal` 包含有效的值; 否则，访问 `m_iVal` 将产生不可靠的结果。

## <a name="cdbvariantm_lval"></a><a name="m_lval"></a>CDBVariant：： m_lVal

存储类型为的值 **`long`** 。

### <a name="remarks"></a>备注

`m_lVal`数据成员属于联合。 在访问之前 `m_lVal` ，请先检查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 设置为 DBVT_LONG，则 `m_lVal` 包含有效的值; 否则，访问 `m_lVal` 将产生不可靠的结果。

## <a name="cdbvariantm_pbinary"></a><a name="m_pbinary"></a>CDBVariant：： m_pbinary

存储指向[CLongBinary](../../mfc/reference/clongbinary-class.md)类型对象的指针。

### <a name="remarks"></a>备注

`m_pbinary`数据成员属于联合。 在访问之前 `m_pbinary` ，请先检查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 设置为 DBVT_BINARY，则 `m_pbinary` 包含有效指针; 否则，访问 `m_pbinary` 将产生不可靠的结果。

## <a name="cdbvariantm_pdate"></a><a name="m_pdate"></a>CDBVariant：： m_pdate

存储指向类型 TIMESTAMP_STRUCT 的对象的指针。

### <a name="remarks"></a>备注

`m_pdate`数据成员属于联合。 在访问之前 `m_pdate` ，请先检查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 设置为 DBVT_DATE，则 `m_pdate` 包含有效指针; 否则，访问 `m_pdate` 将产生不可靠的结果。

有关 TIMESTAMP_STRUCT 数据类型的详细信息，请参阅 Windows SDK 中的*ODBC 程序员参考*的附录 D 中的[C 数据类型](/sql/odbc/reference/appendixes/c-data-types)主题。

## <a name="cdbvariantm_pstring"></a><a name="m_pstring"></a>CDBVariant：： m_pstring

存储指向类型[CString](../../atl-mfc-shared/reference/cstringt-class.md)的对象的指针。

### <a name="remarks"></a>备注

`m_pstring`数据成员属于联合。 在访问之前 `m_pstring` ，请先检查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 设置为 DBVT_STRING，则 `m_pstring` 包含有效指针; 否则，访问 `m_pstring` 将产生不可靠的结果。

## <a name="cdbvariantm_pstringa"></a><a name="m_pstringa"></a>CDBVariant：： m_pstringA

存储指向 ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的指针。

### <a name="remarks"></a>备注

`m_pstringA`数据成员属于联合。 在访问之前 `m_pstringA` ，请先检查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 设置为 DBVT_ASTRING，则 `m_pstringA` 包含有效指针; 否则，访问 `m_pstringA` 将产生不可靠的结果。

## <a name="cdbvariantm_pstringw"></a><a name="m_pstringw"></a>CDBVariant：： m_pstringW

存储指向宽[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的指针。

### <a name="remarks"></a>备注

`m_pstringW`数据成员属于联合。 在访问之前 `m_pstringW` ，请先检查[CDBVariant：： m_dwType](#m_dwtype)的值。 如果 `m_dwType` 设置为 DBVT_WSTRING，则 `m_pstringW` 包含有效指针; 否则，访问 `m_pstringW` 将产生不可靠的结果。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)
