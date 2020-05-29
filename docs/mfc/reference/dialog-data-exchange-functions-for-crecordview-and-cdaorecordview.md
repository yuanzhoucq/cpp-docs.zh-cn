---
title: CRecordView 和 CDaoRecordView 的对话框数据交换函数
ms.date: 09/17/2019
f1_keywords:
- AFXDAO/DDX_FieldCBIndex
- AFXDAO/DDX_FieldCBString
- AFXDAO/DDX_FieldCBStringExact
- AFXDAO/DDX_FieldCheck
- AFXDAO/DDX_FieldLBIndex
- AFXDAO/DDX_FieldLBString
- AFXDAO/DDX_FieldLBStringExact
- AFXDAO/DDX_FieldRadio
- AFXDAO/DDX_FieldScroll
- AFXDAO/DDX_FieldText
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
ms.openlocfilehash: 3128b1ba459cb017d1cdb2321bc55d865aa4f8b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365778"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>CRecordView 和 CDaoRecordView 的对话框数据交换函数

本主题列出了用于在[CRecordset](../../mfc/reference/crecordset-class.md)和[CRecordView](../../mfc/reference/crecordview-class.md)窗体或[CDaoRecordset 窗体](../../mfc/reference/cdaorecordset-class.md)之间交换数据DDX_Field[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)函数。 DAO 与 Access 数据库一起使用，并通过 Office 2013 支持。 DAO 3.6 是最终版本，它被视为过时版本。

> [!NOTE]
> DDX_Field函数类似于 DDX 函数，因为它们与窗体中的控件交换数据。 但与 DDX 不同，它们与视图关联的记录集对象的字段交换数据，而不是与记录视图本身的字段交换数据。 有关详细信息，请参阅 类`CRecordView`和`CDaoRecordView`。

### <a name="ddx_field-functions"></a>DDX_Field功能

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|在[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)中的组合框中，在记录集字段数据成员和当前选择的索引之间传输整数数据。|
|[DDX_FieldCBString](#ddx_fieldcbstring)|在`CString`记录集字段数据成员和`CRecordView`或`CDaoRecordView`中的组合框的编辑控件之间传输数据。 将数据从记录集移动到控件时，此函数将在组合框中选择以指定字符串中的字符开头的项。|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|在`CString`记录集字段数据成员和`CRecordView`或`CDaoRecordView`中的组合框的编辑控件之间传输数据。 将数据从记录集移动到控件时，此函数将在组合框中选择与指定字符串完全匹配的项。|
|[DDX_FieldCheck](#ddx_fieldcheck)|在记录集字段数据成员和`CRecordView`或`CDaoRecordView`中的复选框之间传输布尔数据。|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|在 记录集字段数据成员和`CRecordView`或`CDaoRecordView`中的列表框中的当前所选内容的索引之间传输整数数据。|
|[DDX_FieldLBString](#ddx_fieldlbstring)|管理在列表框控件和记录集的字段数据成员之间传输[CString](../../atl-mfc-shared/reference/cstringt-class.md)数据。 将数据从记录集移动到控件时，此函数将在列表框中选择以指定字符串中的字符开头的项。|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|管理列表框控件`CString`和记录集的字段数据成员之间的数据传输。 将数据从记录集移动到控件时，此函数将选择与指定字符串完全匹配的第一个项。|
|[DDX_FieldRadio](#ddx_fieldradio)|在记录集字段数据成员和`CRecordView`或`CDaoRecordView`中的一组单选按钮之间传输整数数据。|
|[DDX_FieldScroll](#ddx_fieldscroll)|设置或获取`CRecordView`或`CDaoRecordView`中的滚动条控件的滚动位置。 从[DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)功能呼叫。|
|[DDX_FieldSlider](#ddx_fieldslider)|同步记录视图中滑块控件的拇指位置和记录集的`int`字段数据成员。 |
|[DDX_FieldText](#ddx_fieldtext)|重载版本可用于在记录集`int`字段数据成员和`CRecordView`或`CDaoRecordView``DWORD`中的编辑框之间传输 **、UINT、****长** [、CString、](../../atl-mfc-shared/reference/cstringt-class.md)**浮动**、**双**、**短**[、COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)和[COleCurrency](../../mfc/reference/colecurrency-class.md)数据。|

## <a name="ddx_fieldcbindex"></a><a name="ddx_fieldcbindex"></a>DDX_FieldCBIndex

该`DDX_FieldCBIndex`函数同步记录视图中组合框控件的列表框控件中所选项的索引以及与记录视图关联的记录集`int`的字段数据成员。

```cpp
void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象中的控件的 ID。

*index*<br/>
对关联`CRecordset`或`CDaoRecordset`对象中的字段数据成员的引用。

*pRecordset*<br/>
指向与其中交换数据的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象的指针。

### <a name="remarks"></a>备注

将数据从记录集移动到控件时，此函数根据*索引*中指定的值在控件中设置选择。 在从记录集传输到控件时，如果记录集字段为 Null，则 MFC 将索引的值设置为 0。 在从控件传输到记录集时，如果控件为空，或者如果未选择任何项，则记录集字段设置为 0。

如果使用基于 ODBC 的类，请使用第一个版本。 如果使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段的 DDX 的示例和详细信息，请参阅文章["记录视图](../../data/record-views-mfc-data-access.md)"。

### <a name="example"></a>示例

有关一般DDX_Field示例，请参阅[DDX_FieldText。](#ddx_fieldtext) 该示例与 的`DDX_FieldCBIndex`示例类似。

### <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="ddx_fieldcbstring"></a><a name="ddx_fieldcbstring"></a>DDX_FieldCBString

`DDX_FieldCBString` 函数管理记录视图中组合框控件的编辑控件和与记录视图关联的记录集的`CString`字段数据成员之间的[CString](../../atl-mfc-shared/reference/cstringt-class.md)数据传输。 

```cpp
void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象中的控件的 ID。

*value*<br/>
对关联`CRecordset`或`CDaoRecordset`对象中的字段数据成员的引用。

*pRecordset*<br/>
指向与其中交换数据的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象的指针。

### <a name="remarks"></a>备注

将数据从记录集移动到控件时，此函数将组合框中的当前选择设置为以*值*中指定的字符串中的字符开头的第一行。 在从记录集传输到控件时，如果记录集字段为 Null，则从组合框中删除任何选择，组合框的编辑控件设置为空。 在从控件传输到记录集时，如果控件为空，则如果字段允许，记录集字段将设置为 Null。

如果使用基于 ODBC 的类，请使用第一个版本。 如果使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段的 DDX 的示例和详细信息，请参阅文章["记录视图](../../data/record-views-mfc-data-access.md)"。

### <a name="example"></a>示例

有关一般DDX_Field示例，请参阅[DDX_FieldText。](#ddx_fieldtext) 该示例包括对`DDX_FieldCBString`的调用。

### <a name="requirements"></a>要求

  **标题**afxdao.h

## <a name="ddx_fieldcbstringexact"></a><a name="ddx_fieldcbstringexact"></a>DDX_FieldCBStringExact

`DDX_FieldCBStringExact` 函数管理记录视图中组合框控件的编辑控件和与记录视图关联的记录集的`CString`字段数据成员之间的[CString](../../atl-mfc-shared/reference/cstringt-class.md)数据传输。 

```cpp
void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象中的控件的 ID。

*value*<br/>
对关联`CRecordset`或`CDaoRecordset`对象中的字段数据成员的引用。

*pRecordset*<br/>
指向与其中交换数据的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象的指针。

### <a name="remarks"></a>备注

将数据从记录集移动到控件时，此函数将组合框中的当前选择设置为与*值*中指定的字符串完全匹配的第一行。 在从记录集传输到控件时，如果记录集字段为 NULL，则从组合框中删除任何选择，组合框的编辑框设置为空。 在从控件传输到记录集时，如果控件为空，则记录集字段将设置为 NULL。

如果使用基于 ODBC 的类，请使用第一个版本。 如果使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段的 DDX 的示例和详细信息，请参阅文章["记录视图](../../data/record-views-mfc-data-access.md)"。

### <a name="example"></a>示例

有关一般DDX_Field示例，请参阅[DDX_FieldText。](#ddx_fieldtext) 调用`DDX_FieldCBStringExact`将类似。

### <a name="requirements"></a>要求

  **标题**afxdao.h

## <a name="ddx_fieldcheck"></a><a name="ddx_fieldcheck"></a>DDX_FieldCheck

该`DDX_FieldCheck`函数管理在对话框、窗体视图或控件视图对象的复选框控件和对话框、窗体视图或控件视图对象的**int**数据成员之间传输**int**数据。

```cpp
void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的复选框控件的资源 ID。

*value*<br/>
对对话框、窗体视图或控件视图对象的成员变量的引用，用于交换数据。

*pRecordset*<br/>
指向与其中交换数据的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象的指针。

### <a name="remarks"></a>备注

调用`DDX_FieldCheck`时，*值*设置为复选框控件的当前状态，或者控件的状态设置为*值*，具体取决于传输方向。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdao.h

## <a name="ddx_fieldlbindex"></a><a name="ddx_fieldlbindex"></a>DDX_FieldLBIndex

该`DDX_FieldLBIndex`函数同步记录视图中的列表框控件中所选项的索引以及与记录视图关联的记录集的**int**字段数据成员。

```cpp
void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象中的控件的 ID。

*index*<br/>
对关联`CRecordset`或`CDaoRecordset`对象中的字段数据成员的引用。

*pRecordset*<br/>
指向与其中交换数据的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象的指针。

### <a name="remarks"></a>备注

将数据从记录集移动到控件时，此函数根据*索引*中指定的值在控件中设置选择。 在从记录集传输到控件时，如果记录集字段为 Null，则 MFC 将索引的值设置为 0。 在从控件传输到记录集时，如果控件为空，则记录集字段设置为 0。

如果使用基于 ODBC 的类，请使用第一个版本。 如果使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段的 DDX 的示例和详细信息，请参阅文章["记录视图](../../data/record-views-mfc-data-access.md)"。

### <a name="example"></a>示例

有关一般DDX_Field示例，请参阅[DDX_FieldText。](#ddx_fieldtext)

### <a name="requirements"></a>要求

  **标题**afxdao.h

## <a name="ddx_fieldlbstring"></a><a name="ddx_fieldlbstring"></a>DDX_FieldLBString

`DDX_FieldLBString`将记录视图中列表框控件的当前选定内容 复制到与记录视图关联的记录集的[CString](../../atl-mfc-shared/reference/cstringt-class.md)字段数据成员中。

```cpp
void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象中的控件的 ID。

*value*<br/>
对关联`CRecordset`或`CDaoRecordset`对象中的字段数据成员的引用。

*pRecordset*<br/>
指向与其中交换数据的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象的指针。

### <a name="remarks"></a>备注

在相反的方向上，此函数将列表框中的当前选择设置为以*值*指定的字符串中的字符开头的第一行。 在从记录集传输到控件时，如果记录集字段为 Null，则从列表框中删除任何选择。 在从控件传输到记录集时，如果控件为空，则记录集字段将设置为 Null。

如果使用基于 ODBC 的类，请使用第一个版本。 如果使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段的 DDX 的示例和详细信息，请参阅文章["记录视图](../../data/record-views-mfc-data-access.md)"。

### <a name="example"></a>示例

有关一般DDX_Field示例，请参阅[DDX_FieldText。](#ddx_fieldtext) 调用`DDX_FieldLBString`将类似。

### <a name="requirements"></a>要求

  **标题**afxdao.h

## <a name="ddx_fieldlbstringexact"></a><a name="ddx_fieldlbstringexact"></a>DDX_FieldLBStringExact

`DDX_FieldLBStringExact`函数将记录视图中列表框控件的当前选定内容复制到与记录视图关联的记录集的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 字段数据成员中。  

```cpp
void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象中的控件的 ID。

*value*<br/>
对关联`CRecordset`或`CDaoRecordset`对象中的字段数据成员的引用。

*pRecordset*<br/>
指向与其中交换数据的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象的指针。

### <a name="remarks"></a>备注

在相反的方向上，此函数将列表框中的当前选择设置为与*值*中指定的字符串完全相同的第一行。 在从记录集传输到控件时，如果记录集字段为 Null，则从列表框中删除任何选择。 在从控件传输到记录集时，如果控件为空，则记录集字段将设置为 Null。

如果使用基于 ODBC 的类，请使用第一个版本。 如果使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段的 DDX 的示例和详细信息，请参阅文章["记录视图](../../data/record-views-mfc-data-access.md)"。

### <a name="example"></a>示例

有关一般DDX_Field示例，请参阅[DDX_FieldText。](#ddx_fieldtext) 调用`DDX_FieldLBStringExact`将类似。

### <a name="requirements"></a>要求

  **标题**afxdao.h

## <a name="ddx_fieldradio"></a><a name="ddx_fieldradio"></a>DDX_FieldRadio

该`DDX_FieldRadio`函数将记录视图的记录集的零基**int**成员变量与记录视图中一组单选按钮中的当前选定的单选按钮关联。

```cpp
void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView 或 CDaoRecordView](../../mfc/reference/crecordview-class.md)对象中相邻单选按钮控件组中的第一个（具有[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)样式WS_GROUP）的 ID。

*value*<br/>
对关联`CRecordset`或`CDaoRecordset`对象中的字段数据成员的引用。

*pRecordset*<br/>
指向与其中交换数据的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象的指针。

### <a name="remarks"></a>备注

从记录集字段传输到视图时，此功能将打开*第 n 个*单选按钮（从零开始），然后关闭其他按钮。 在相反的方向上，此函数将记录集字段设置为当前打开（已选中）的单选按钮的定单数。 在从记录集传输到控件时，如果记录集字段为"空"，则不选择任何按钮。 在从控件传输到记录集时，如果未选择控件，则如果字段允许，记录集字段将设置为 Null。

如果使用基于 ODBC 的类，请使用第一个版本。 如果使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段的 DDX 的示例和详细信息，请参阅文章["记录视图](../../data/record-views-mfc-data-access.md)"。

### <a name="example"></a>示例

有关一般DDX_Field示例，请参阅[DDX_FieldText。](#ddx_fieldtext) 调用`DDX_FieldRadio`将类似。

### <a name="requirements"></a>要求

  **标题**afxdao.h

## <a name="ddx_fieldscroll"></a><a name="ddx_fieldscroll"></a>DDX_FieldScroll

该`DDX_FieldScroll`函数同步记录视图中滚动条控件的滚动位置以及与记录视图关联的记录集**的 int**字段数据成员（或与选择映射到它的任何整数变量一起）。

```cpp
void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView 或 CDaoRecordView](../../mfc/reference/crecordview-class.md)对象中相邻单选按钮控件组中的第一个（具有[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)样式WS_GROUP）的 ID。

*value*<br/>
对关联`CRecordset`或`CDaoRecordset`对象中的字段数据成员的引用。

*pRecordset*<br/>
指向与其中交换数据的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象的指针。

### <a name="remarks"></a>备注

将数据从记录集移动到控件时，此函数将滚动条控件的滚动位置设置为值 中指定的*值*。 在从记录集传输到控件时，如果记录集字段为 Null，则滚动条控件设置为 0。 在从控件传输到记录集时，如果控件为空，则记录集字段的值为 0。

如果使用基于 ODBC 的类，请使用第一个版本。 如果使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段的 DDX 的示例和详细信息，请参阅文章["记录视图](../../data/record-views-mfc-data-access.md)"。

### <a name="example"></a>示例

有关一般DDX_Field示例，请参阅[DDX_FieldText。](#ddx_fieldtext) 调用`DDX_FieldScroll`将类似。

### <a name="requirements"></a>要求

  **标题**afxdao.h

## <a name="ddx_fieldslider"></a><a name="ddx_fieldslider"></a>DDX_FieldSlider

该`DDX_FieldSlider`函数同步记录视图中滑块控件的拇指位置以及与记录视图关联的记录集**的 int**字段数据成员（或与选择映射到的任何整数变量一起）。

### <a name="syntax"></a>语法

```cpp
void AFXAPI DDX_FieldSlider(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset );

void AFXAPI DDX_FieldSlider(
   CDataExchange* pDX,
   int nIDC,
   int& value,
   CDaoRecordset* pRecordset );
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
滑块控件的资源 ID。

*value*<br/>
对要交换的值的引用。 此参数保留或将用于设置滑块控件的当前拇指位置。

*pRecordset*<br/>
指向与其交换数据的关联`CRecordset`或`CDaoRecordset`对象的指针。

### <a name="remarks"></a>备注

将数据从记录集移动到滑块时，此函数将滑块的位置设置为值 中指定的*值*。 在从记录集传输到控件时，如果记录集字段为 Null，则滑块控件的位置设置为 0。 在从控件传输到记录集时，如果控件为空，则记录集字段的值为 0。

`DDX_FieldSlider`不会使用能够设置范围的滑块控件交换范围信息，而不仅仅是位置。

如果使用基于 ODBC 的类，请使用函数的第一个重写。 使用第二个覆盖与基于 DAO 的类。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../dialog-data-exchange-and-validation.md)。 有关 DDX 和`CRecordView``CDaoRecordView`字段的详细信息，请参阅[记录视图](../../data/record-views-mfc-data-access.md)。 有关滑块控件的信息，请参阅[使用 CSliderCtrl](../using-csliderctrl.md)。

### <a name="example"></a>示例

有关一般DDX_Field示例，请参阅[DDX_FieldText。](#ddx_fieldtext) 调用`DDX_FieldSlider`将类似。

### <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="ddx_fieldtext"></a><a name="ddx_fieldtext"></a>DDX_FieldText

`DDX_FieldText`************       函数管理在编辑框控件和的字段数据成员之间进行 int、short、long、DWORD、[CString](../../atl-mfc-shared/reference/cstringt-class.md)****************、float、double、BOOL 或 BYTE 数据的传输记录集.

```cpp
void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    UINT& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    short& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BOOL& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象中的控件的 ID。

*value*<br/>
对关联`CRecordset`或`CDaoRecordset`对象中的字段数据成员的引用。 值的数据类型取决于`DDX_FieldText`您使用的重载版本。

*pRecordset*<br/>
指向与其中交换数据的[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象的指针。 此指针允许`DDX_FieldText`检测和设置 Null 值。

### <a name="remarks"></a>备注

对于[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) `DDX_FieldText`对象，还要管理传输[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)和[COle货币](../../mfc/reference/colecurrency-class.md)值。 空编辑框控件指示空值。 在从记录集传输到控件时，如果记录集字段为 Null，则编辑框设置为空。 在从控件传输到记录集时，如果控件为空，则记录集字段将设置为 Null。

如果使用基于 ODBC 的类，请使用具有[CRecordset](../../mfc/reference/crecordset-class.md)参数的版本。 如果使用基于 DAO 的类，请使用具有[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)参数的版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关[CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段的 DDX 的示例和详细信息，请参阅文章["记录视图](../../data/record-views-mfc-data-access.md)"。

### <a name="example"></a>示例

[CRecordView](../../mfc/reference/crecordview-class.md) 的以下`DoDataExchange`函数包含 三种数据类型的`DDX_FieldText`函数调用：`IDC_COURSELIST` 是一个组合框; 另两个控件是编辑框。 对于 DAO 编程 *，m_pSet*参数是指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset 的](../../mfc/reference/cdaorecordset-class.md)指针。

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>要求

  **标题**afxdao.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](mfc-macros-and-globals.md)
