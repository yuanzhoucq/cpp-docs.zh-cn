---
title: CRecordView 和 CDaoRecordView 的对话框数据交换函数
ms.date: 11/04/2016
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
ms.openlocfilehash: 36341a1b122e6dcb1c475f2f95e03d384c3a034f
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850030"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>CRecordView 和 CDaoRecordView 的对话框数据交换函数

本主题列出了用于之间交换数据的 DDX_Field 函数[CRecordset](../../mfc/reference/crecordset-class.md)和一个[CRecordView](../../mfc/reference/crecordview-class.md)窗体或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)窗体。

> [!NOTE]
>  DDX_Field 函数是与 DDX 函数一样的在交换与窗体控件中的数据。 但是，它们与不同的 DDX，交换数据的视图关联的记录集对象的字段而不是使用记录视图本身的字段。 有关详细信息，请参见类`CRecordView`和`CDaoRecordView`。

### <a name="ddxfield-functions"></a>DDX_Field 函数

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|传输整型数据记录集字段数据成员和组合框中当前所选内容的索引之间[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)。|
|[DDX_FieldCBString](#ddx_fieldcbstring)|传输`CString`记录集字段数据成员和一个组合的编辑控件之间的数据框中`CRecordView`或`CDaoRecordView`。 移动数据时从记录集到控件，此函数以指定字符串中字符的组合框中选择的项。|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|传输`CString`记录集字段数据成员和一个组合的编辑控件之间的数据框中`CRecordView`或`CDaoRecordView`。 移动数据时从记录集到控件，此函数在与指定的字符串完全匹配的组合框中选择的项。|
|[DDX_FieldCheck](#ddx_fieldcheck)|传输布尔数据之间的记录集字段数据成员和中的复选框`CRecordView`或`CDaoRecordView`。|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|传输整型数据记录集字段数据成员和列表框中当前所选内容的索引之间`CRecordView`或`CDaoRecordView`。|
|[DDX_FieldLBString](#ddx_fieldlbstring)|管理的传输[CString](../../atl-mfc-shared/reference/cstringt-class.md)列表框控件和记录集的字段数据成员之间的数据。 移动数据时从记录集到控件，此函数中指定的字符串的字符开始在列表框中选择的项。|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|管理的传输`CString`列表框控件和记录集的字段数据成员之间的数据。 移动数据时从记录集到控件，此函数将选择与指定的字符串完全匹配的第一项。|
|[DDX_FieldRadio](#ddx_fieldradio)|传输整型数据记录集字段数据成员和一组中的单选按钮之间`CRecordView`或`CDaoRecordView`。|
|[DDX_FieldScroll](#ddx_fieldscroll)|设置或获取滚动条控件中的滚动位置`CRecordView`或`CDaoRecordView`。 从调用你[DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)函数。|
|[DDX_FieldSlider](#ddx_fieldslider)|同步缩略图的滑块控件中的记录视图位置和一个`int`的记录集字段数据成员。 |
|[DDX_FieldText](#ddx_fieldtext)|重载的版本都是可用于传输`int`， **UINT**，**长**， `DWORD`， [CString](../../atl-mfc-shared/reference/cstringt-class.md)， **float****双**，**短**， [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)，以及[COleCurrency](../../mfc/reference/colecurrency-class.md)之间的记录集字段数据成员和编辑数据框中`CRecordView`或`CDaoRecordView`。|

##  <a name="ddx_fieldcbindex"></a>  DDX_FieldCBIndex

`DDX_FieldCBIndex`函数将同步记录视图中的组合框控件的列表框控件中的选定项的索引和`int`的记录集与记录视图关联的字段数据成员。

```
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
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。

*index*<br/>
对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。

*pRecordset*<br/>
一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。

### <a name="remarks"></a>备注

此函数时将数据从记录集移到控件，设置基于中指定的值在控件中选择*索引*。 上从记录集传输到该控件后，如果记录集字段为 Null，MFC 设置索引的值为 0。 上从控件传输到记录集后，该控件是否为空或未选择任何项，记录集字段设置为 0。

如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)并[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>示例

请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 示例。 该示例将类似的`DDX_FieldCBIndex`。

### <a name="requirements"></a>要求

**标头：** afxdao.h

##  <a name="ddx_fieldcbstring"></a>  DDX_FieldCBString

`DDX_FieldCBString`函数管理传输[CString](../../atl-mfc-shared/reference/cstringt-class.md)记录视图中的组合框控件的编辑控件之间的数据和`CString`的记录集与记录视图关联的字段数据成员。

```
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
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。

*值*<br/>
对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。

*pRecordset*<br/>
一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。

### <a name="remarks"></a>备注

此函数时将数据从记录集移到控件，组合框中指定的字符串中字符开头的第一行中设置当前所选内容*值*。 在从记录集的传输到该控件，如果记录集字段为 Null，从组合框中删除任何选择和组合框编辑控件将设置为空。 上从控件传输到记录集后，如果该控件为空，记录集字段是如果设置为 Null 字段允许。

如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)并[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>示例

请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 示例。 该示例包含对的调用`DDX_FieldCBString`。

### <a name="requirements"></a>要求

  **标头**afxdao.h

## <a name="ddx_fieldcbstringexact"></a>  DDX_FieldCBStringExact

`DDX_FieldCBStringExact`函数管理传输[CString](../../atl-mfc-shared/reference/cstringt-class.md)记录视图中的组合框控件的编辑控件之间的数据和`CString`的记录集与记录视图关联的字段数据成员。

```
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
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。

*值*<br/>
对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。

*pRecordset*<br/>
一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。

### <a name="remarks"></a>备注

此函数时将数据从记录集移到控件，与中指定的字符串完全匹配的第一行的组合框中设置当前所选内容*值*。 在从记录集的传输到该控件，如果记录集字段为 NULL，从组合框中删除任何所选内容和设置组合框的编辑框为空。 上从控件传输到记录集后，如果该控件为空，记录集字段设置为 NULL。

如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)并[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>示例

请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 示例。 调用`DDX_FieldCBStringExact`类似。

### <a name="requirements"></a>要求

  **标头**afxdao.h

##  <a name="ddx_fieldcheck"></a>  DDX_FieldCheck

`DDX_FieldCheck`函数管理传输**int**对话框中中的复选框控件之间的数据窗体视图或控件视图对象和一个**int**对话框、 窗体视图或控件的数据成员视图对象。

```
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
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的复选框控件的资源 ID。

*值*<br/>
对对话框、 窗体视图或控件视图对象与其交换数据的成员变量的引用。

*pRecordset*<br/>
一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。

### <a name="remarks"></a>备注

当`DDX_FieldCheck`调用时，*值*设置为当前状态的复选框控件或控件的状态设置为*值*，取决于传输的方向。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdao.h

##  <a name="ddx_fieldlbindex"></a>  DDX_FieldLBIndex

`DDX_FieldLBIndex`函数将同步记录视图的列表框控件中的选定项的索引和一个**int**的记录集与记录视图关联的字段数据成员。

```
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
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。

*index*<br/>
对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。

*pRecordset*<br/>
一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。

### <a name="remarks"></a>备注

此函数时将数据从记录集移到控件，设置基于中指定的值在控件中选择*索引*。 上从记录集传输到该控件后，如果记录集字段为 Null，MFC 设置索引的值为 0。 上从控件传输到记录集后，如果该控件为空，记录集字段设置为 0。

如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)并[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>示例

请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 示例。

### <a name="requirements"></a>要求

  **标头**afxdao.h

##  <a name="ddx_fieldlbstring"></a>  DDX_FieldLBString

`DDX_FieldLBString`将列表框控件的当前选定内容复制到记录视图中[CString](../../atl-mfc-shared/reference/cstringt-class.md)的记录集与记录视图关联的字段数据成员。

```
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
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。

*值*<br/>
对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。

*pRecordset*<br/>
一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。

### <a name="remarks"></a>备注

按反向执行此函数所设置的列表框中指定的字符串字符开头的第一行中的当前所选内容*值*。 上从记录集传输到该控件后，如果记录集字段为 Null，任何所选内容已从列表框。 上从控件传输到记录集后，如果该控件为空，记录集字段设置为 Null。

如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)并[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>示例

请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 示例。 调用`DDX_FieldLBString`类似。

### <a name="requirements"></a>要求

  **标头**afxdao.h

##  <a name="ddx_fieldlbstringexact"></a>  DDX_FieldLBStringExact

`DDX_FieldLBStringExact`函数将列表框控件的当前所选内容复制到记录视图中[CString](../../atl-mfc-shared/reference/cstringt-class.md)的记录集与记录视图关联的字段数据成员。

```
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
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。

*值*<br/>
对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。

*pRecordset*<br/>
一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。

### <a name="remarks"></a>备注

按反向执行此函数设置当前所选内容中与中指定的字符串完全匹配的第一行的列表框*值*。 上从记录集传输到该控件后，如果记录集字段为 Null，任何所选内容已从列表框。 上从控件传输到记录集后，如果该控件为空，记录集字段设置为 Null。

如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)并[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>示例

请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 示例。 调用`DDX_FieldLBStringExact`类似。

### <a name="requirements"></a>要求

  **标头**afxdao.h

##  <a name="ddx_fieldradio"></a>  DDX_FieldRadio

`DDX_FieldRadio`函数将从零开始**int**的一组记录视图中的单选按钮中的当前所选的单选按钮的记录视图的记录集的成员变量。

```
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
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
第一个的 ID （具有样式 WS_GROUP） 中的相邻的单选按钮控件的组中[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。

*值*<br/>
对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。

*pRecordset*<br/>
一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。

### <a name="remarks"></a>备注

传输时从记录集字段的视图，此函数将开启*第 n 个*（从零开始） 的单选按钮并关闭其他按钮。 按反向执行此函数将记录集字段设置为当前的 （选中） 的单选按钮的初始数字。 在从记录集传输到该控件后，如果记录集字段为 Null，没有按钮被选定。 上从控件传输到记录集后，如果没有选定，记录集字段是如果设置为 Null 字段允许的。

如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)并[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>示例

请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 示例。 调用`DDX_FieldRadio`类似。

### <a name="requirements"></a>要求

  **标头**afxdao.h

##  <a name="ddx_fieldscroll"></a>  DDX_FieldScroll

`DDX_FieldScroll`函数将同步记录视图中滚动条控件的滚动位置和一个**int**的记录集与记录视图 （或您选择将其映射到任何整数变量） 关联的字段数据成员.

```
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
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
第一个的 ID （具有样式 WS_GROUP） 中的相邻的单选按钮控件的组中[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。

*值*<br/>
对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。

*pRecordset*<br/>
一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。

### <a name="remarks"></a>备注

此函数时将数据从记录集移到控件，将滚动条控件的滚动位置设置为中指定的值*值*。 上从记录集传输到该控件后，如果记录集字段为 Null，滚动条控件设置为 0。 在从控件传输到记录集后，如果该控件为空，记录集字段的值为 0。

如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)并[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>示例

请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 示例。 调用`DDX_FieldScroll`类似。

### <a name="requirements"></a>要求

  **标头**afxdao.h

  ## <a name="ddx_fieldslider"></a>  DDX_FieldSlider
`DDX_FieldSlider`函数将同步缩略图的滑块控件中的记录视图位置和一个**int**的记录集与记录视图 （或您选择将其映射到任何整数变量） 关联的字段数据成员。

### <a name="syntax"></a>语法

  ```
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
一个指向[CDataExchange](cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
滑块控件的资源 ID。

*值*<br/>
对值进行交换的引用。 此参数保留或将用于设置滑块控件的滚动块的当前位置。

*pRecordset*<br/>
一个指向关联`CRecordset`或`CDaoRecordset`与其交换数据的对象。

### <a name="remarks"></a>备注

此函数时将数据从记录集移动到滑块，将滑块的位置设置为在指定的值*值*。 上从记录集传输到该控件后，如果记录集字段为 Null，滑块控件的位置设置为 0。 在从控件传输到记录集后，如果该控件为空，记录集字段的值为 0。

`DDX_FieldSlider` 不交换与滑块控件支持的设置范围而不是只需一个位置的范围信息。

如果你正在使用基于 ODBC 的类，请使用函数的第一个重写。 第二个重写使用基于 DAO 的类。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX`CRecordView`并`CDaoRecordView`字段，请参阅[记录视图](../../data/record-views-mfc-data-access.md)。 滑块控件有关的信息，请参阅[使用 CSliderCtrl](../using-csliderctrl.md)。

### <a name="example"></a>示例

请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 示例。 调用`DDX_FieldSlider`类似。

### <a name="requirements"></a>要求

**标头：** afxdao.h

##  <a name="ddx_fieldtext"></a>  DDX_FieldText

`DDX_FieldText`函数管理传输**int**，**短**，**长**，DWORD， [CString](../../atl-mfc-shared/reference/cstringt-class.md)， **float**，**双**， **BOOL**，或**字节**的编辑框控件和记录集的字段数据成员之间的数据。

```
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
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。

*值*<br/>
对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。 值的数据类型取决于其的重载版本`DDX_FieldText`你使用。

*pRecordset*<br/>
一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。 此指针使`DDX_FieldText`来检测和设置 Null 值。

### <a name="remarks"></a>备注

有关[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象，`DDX_FieldText`还可管理传输[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)，并且[COleCurrency](../../mfc/reference/colecurrency-class.md)值。 一个空的编辑框控件指示 Null 值。 上从记录集传输到该控件后，如果记录集字段为 Null，在编辑框设置为空。 上从控件传输到记录集后，如果该控件为空，记录集字段设置为 Null。

使用的版本与[CRecordset](../../mfc/reference/crecordset-class.md)参数，如果你正在使用基于 ODBC 的类。 使用的版本与[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)参数，如果你正在使用基于 DAO 的类。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)并[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。

### <a name="example"></a>示例

以下`DoDataExchange`函数[CRecordView](../../mfc/reference/crecordview-class.md)包含`DDX_FieldText`函数调用的三个数据类型：`IDC_COURSELIST`是一个组合框; 其他两个控件的编辑框。 DAO 编程*m_pSet*参数是指向指针[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>要求

  **标头**afxdao.h

## <a name="see-also"></a>请参阅

[宏和全局函数](mfc-macros-and-globals.md)
