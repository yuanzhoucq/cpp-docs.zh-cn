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
ms.openlocfilehash: 3c13c1a965014af271ce2911505742d9a50eedd7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376449"
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
|[CDB 变量：：CDB 变量](#cdbvariant)|构造 `CDBVariant` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDB 变量：清除](#clear)|清除`CDBVariant`对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CDB 变量：：m_dwType](#m_dwtype)|包含当前存储值的数据类型。 键入 `DWORD`。|

### <a name="public-union-members"></a>公共工会成员

|名称|说明|
|----------|-----------------|
|[国开行：：m_boolVal](#m_boolval)|包含**BOOL**类型的值。|
|[CDB 变量：：m_chVal](#m_chval)|包含类型**无符号字符**的值。|
|[CDB 变量：：m_dblVal](#m_dblval)|包含**双精度**类型的值。|
|[CDB 变量：：m_fltVal](#m_fltval)|包含类型**浮点**的值。|
|[CDB 变量：：m_iVal](#m_ival)|包含**短类型**的值。|
|[CDB变量：：m_lVal](#m_lval)|包含**长**类型的值。|
|[CDB 变量：m_pbinary](#m_pbinary)|包含指向类型`CLongBinary`对象的指针。|
|[国开行：：m_pdate](#m_pdate)|包含指向类型**TIMESTAMP_STRUCT对象的指针**。|
|[国开行：：m_pstring](#m_pstring)|包含指向类型`CString`对象的指针。|
|[CDB 变量：：m_pstringA](#m_pstringa)|存储指向 ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的指针。|
|[CDB 变量：：m_pstringW](#m_pstringw)|存储指向宽[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的指针。|

## <a name="remarks"></a>备注

`CDBVariant`没有基类。

`CDBVariant`类似于[COleVariant;](../../mfc/reference/colevariant-class.md)但是，`CDBVariant`不使用 OLE。 `CDBVariant`允许您存储值，而不必担心该值的数据类型。 `CDBVariant`跟踪存储在联合中的当前值的数据类型。

CRecordset[类](../../mfc/reference/crecordset-class.md)`CDBVariant`利用三个成员函数中的对象： `GetFieldValue``GetBookmark`和`SetBookmark`。 例如，`GetFieldValue`允许您动态提取列中的数据。 由于列的数据类型在运行时可能不知道，因此`GetFieldValue`使用`CDBVariant`对象来存储列的数据。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CDBVariant`

## <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="cdbvariantcdbvariant"></a><a name="cdbvariant"></a>CDB 变量：：CDB 变量

创建 NULL`CDBVariant`对象。

```
CDBVariant();
```

### <a name="remarks"></a>备注

将[m_dwType](#m_dwtype)数据成员设置为DBVT_NULL。

## <a name="cdbvariantclear"></a><a name="clear"></a>CDB 变量：清除

调用此成员函数以清除`CDBVariant`对象。

```
void Clear();
```

### <a name="remarks"></a>备注

如果[m_dwType](#m_dwtype)数据成员的值是DBVT_DATE、DBVT_STRING或DBVT_BINARY，则`Clear`释放与联合指针成员关联的内存。 `Clear`设置`m_dwType`到DBVT_NULL。

析`CDBVariant`构函数调用`Clear`。

## <a name="cdbvariantm_boolval"></a><a name="m_boolval"></a>国开行：：m_boolVal

存储 BOOL 类型的值。

### <a name="remarks"></a>备注

数据`m_boolVal`成员属于联合。 在访问`m_boolVal`之前，首先检查[CDB 变量的值：：：m_dwType](#m_dwtype)。 如果`m_dwType`设置为DBVT_BOOL，则`m_boolVal`将包含一个有效的值;如果设置为"DBVT_BOOL"，则将包含一个有效值。否则，访问`m_boolVal`将产生不可靠的结果。

## <a name="cdbvariantm_chval"></a><a name="m_chval"></a>CDB 变量：：m_chVal

存储类型**无符号字符**的值。

### <a name="remarks"></a>备注

数据`m_chVal`成员属于联合。 在访问`m_chVal`之前，首先检查[CDB 变量的值：：：m_dwType](#m_dwtype)。 如果`m_dwType`设置为DBVT_UCHAR，则包含有效的`m_chVal`值;如果设置为"DBVT_UCHAR"，则包含一个有效值。否则，访问`m_chVal`将产生不可靠的结果。

## <a name="cdbvariantm_dblval"></a><a name="m_dblval"></a>CDB 变量：：m_dblVal

存储类型**为双**的值。

### <a name="remarks"></a>备注

数据`m_dblVal`成员属于联合。 在访问`m_dblVal`之前，首先检查[CDB 变量的值：：：m_dwType](#m_dwtype)。 如果`m_dwType`设置为DBVT_DOUBLE，则包含有效的`m_dblVal`值;如果设置为"DBVT_DOUBLE"，则包含一个有效值。否则，访问`m_dblVal`将产生不可靠的结果。

## <a name="cdbvariantm_dwtype"></a><a name="m_dwtype"></a>CDB 变量：：m_dwType

此数据成员包含当前存储在`CDBVariant`对象的联合数据成员中的值的数据类型。

### <a name="remarks"></a>备注

在访问此联合之前，必须检查 的值`m_dwType`，以确定要访问哪个联合数据成员。 下表列出了 和`m_dwType`相应的联合数据成员的可能值和相应的联合数据成员。

|m_dwType|联盟数据成员|
|---------------|-----------------------|
|DBVT_NULL|没有工会成员对访问有效。|
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

## <a name="cdbvariantm_fltval"></a><a name="m_fltval"></a>CDB 变量：：m_fltVal

存储类型**浮点**的值。

### <a name="remarks"></a>备注

数据`m_fltVal`成员属于联合。 在访问`m_fltVal`之前，首先检查[CDB 变量的值：：：m_dwType](#m_dwtype)。 如果`m_dwType`设置为DBVT_SINGLE，则包含有效的`m_fltVal`值;如果设置为 DBVT_SINGLE，则包含一个有效值。否则，访问`m_fltVal`将产生不可靠的结果。

## <a name="cdbvariantm_ival"></a><a name="m_ival"></a>CDB 变量：：m_iVal

存储类型**为短**的值。

### <a name="remarks"></a>备注

数据`m_iVal`成员属于联合。 在访问`m_iVal`之前，首先检查[CDB 变量的值：：：m_dwType](#m_dwtype)。 如果`m_dwType`设置为DBVT_SHORT，则包含有效的`m_iVal`值;如果设置为"DBVT_SHORT"，则包含一个有效值。否则，访问`m_iVal`将产生不可靠的结果。

## <a name="cdbvariantm_lval"></a><a name="m_lval"></a>CDB变量：：m_lVal

存储**长**类型的值。

### <a name="remarks"></a>备注

数据`m_lVal`成员属于联合。 在访问`m_lVal`之前，首先检查[CDB 变量的值：：：m_dwType](#m_dwtype)。 如果`m_dwType`设置为DBVT_LONG，则包含有效的`m_lVal`值;如果设置为 DBVT_LONG，则包含一个有效值。否则，访问`m_lVal`将产生不可靠的结果。

## <a name="cdbvariantm_pbinary"></a><a name="m_pbinary"></a>CDB 变量：m_pbinary

存储指向[CLongBinary](../../mfc/reference/clongbinary-class.md)类型的对象的指针。

### <a name="remarks"></a>备注

数据`m_pbinary`成员属于联合。 在访问`m_pbinary`之前，首先检查[CDB 变量的值：：：m_dwType](#m_dwtype)。 如果`m_dwType`设置为DBVT_BINARY，则`m_pbinary`包含有效的指针;否则，访问`m_pbinary`将产生不可靠的结果。

## <a name="cdbvariantm_pdate"></a><a name="m_pdate"></a>国开行：：m_pdate

存储指向类型TIMESTAMP_STRUCT对象的指针。

### <a name="remarks"></a>备注

数据`m_pdate`成员属于联合。 在访问`m_pdate`之前，首先检查[CDB 变量的值：：：m_dwType](#m_dwtype)。 如果`m_dwType`设置为DBVT_DATE，则`m_pdate`包含有效的指针;否则，访问`m_pdate`将产生不可靠的结果。

有关TIMESTAMP_STRUCT数据类型的详细信息，请参阅 Windows SDK 中*ODBC 程序员参考*附录 D 中的主题[C 数据类型](/sql/odbc/reference/appendixes/c-data-types)。

## <a name="cdbvariantm_pstring"></a><a name="m_pstring"></a>国开行：：m_pstring

存储指向[CString](../../atl-mfc-shared/reference/cstringt-class.md)类型的对象的指针。

### <a name="remarks"></a>备注

数据`m_pstring`成员属于联合。 在访问`m_pstring`之前，首先检查[CDB 变量的值：：：m_dwType](#m_dwtype)。 如果`m_dwType`设置为DBVT_STRING，则`m_pstring`包含有效的指针;否则，访问`m_pstring`将产生不可靠的结果。

## <a name="cdbvariantm_pstringa"></a><a name="m_pstringa"></a>CDB 变量：：m_pstringA

存储指向 ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的指针。

### <a name="remarks"></a>备注

数据`m_pstringA`成员属于联合。 在访问`m_pstringA`之前，首先检查[CDB 变量的值：：：m_dwType](#m_dwtype)。 如果`m_dwType`设置为DBVT_ASTRING，则`m_pstringA`包含有效的指针;否则，访问`m_pstringA`将产生不可靠的结果。

## <a name="cdbvariantm_pstringw"></a><a name="m_pstringw"></a>CDB 变量：：m_pstringW

存储指向宽[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的指针。

### <a name="remarks"></a>备注

数据`m_pstringW`成员属于联合。 在访问`m_pstringW`之前，首先检查[CDB 变量的值：：：m_dwType](#m_dwtype)。 如果`m_dwType`设置为DBVT_WSTRING，则`m_pstringW`包含有效的指针;否则，访问`m_pstringW`将产生不可靠的结果。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)
