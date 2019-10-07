---
title: 标准对话框数据交换例程
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 47586f9cff0fcbe2cd7bad31f3d93fed08190830
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511584"
---
# <a name="standard-dialog-data-exchange-routines"></a>标准对话框数据交换例程

本主题列出了用于常见 MFC 对话控件的标准对话框数据交换（DDX）例程。

> [!NOTE]
>  标准对话框数据交换例程在头文件 afxdd_ 中定义。 但是，应用程序应包含 afxwin.h。

### <a name="ddx-functions"></a>DDX 函数

|||
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|初始化或检索组合框控件的当前选定内容的索引。|
|[DDX_CBString](#ddx_cbstring)|初始化或检索组合框控件的编辑字段的当前内容。|
|[DDX_CBStringExact](#ddx_cbstringexact)|初始化或检索组合框控件的编辑字段的当前内容。|
|[DDX_Check](#ddx_check)|初始化或检索复选框控件的当前状态。|
|[DDX_Control](#ddx_control)|向对话框中的给定控件提供子类。|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|初始化或检索日期和时间选择器控件的日期和/或时间数据。|
|[DDX_IPAddress](#ddx_ipaddress)|初始化或检索 IP 地址控件的当前值。|
|[DDX_LBIndex](#ddx_lbindex)|初始化或检索列表框控件当前选定内容的索引。|
|[DDX_LBString](#ddx_lbstring)|初始化或检索列表框控件中的当前选定内容。|
|[DDX_LBStringExact](#ddx_lbstringexact)|初始化或检索列表框控件中的当前选定内容。|
|[DDX_ManagedControl](#ddx_managedcontrol)|创建与控件的资源 ID 相匹配的 .NET 控件。|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|初始化或检索月历控件的当前值。|
|[DDX_Radio](#ddx_radio)|初始化或检索单选控件组中当前选中的单选控件的从零开始的索引。|
|[DDX_Scroll](#ddx_scroll)|初始化或检索滚动控件的滚动块的当前位置。|
|[DDX_Slider](#ddx_slider)|初始化或检索滑块控件的滚动块的当前位置。|
|[DDX_Text](#ddx_text)|初始化或检索编辑控件的当前值。|

##  <a name="ddx_cbindex"></a>  DDX_CBIndex

函数管理对话框、窗体视图或控件视图对象中的组合框控件与对话框、窗体视图或控件视图对象的**int**数据成员之间的 int 数据的传输。 `DDX_CBIndex`

```
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的组合框控件的资源 ID。

*index*<br/>
对用于交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

调用`DDX_CBIndex`时， *index*设置为当前组合框选择的索引。 如果未选择任何项，则*index*设置为0。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

##  <a name="ddx_cbstring"></a>DDX_CBString

函数管理对话框、窗体`CString`视图或`CString`控件视图对象中组合框控件的编辑控件与对话框、窗体视图或控件视图对象的数据成员之间的数据传输。 `DDX_CBString`

```
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的组合框控件的资源 ID。

*value*<br/>
对用于交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

调用`DDX_CBString`时， *value*设置为当前组合框选择。 如果未选择任何项，则将*值*设置为长度为零的字符串。

> [!NOTE]
>  如果组合框为下拉列表框，则交换的值限制为255个字符。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

##  <a name="ddx_cbstringexact"></a>  DDX_CBStringExact

函数管理对话框、窗体`CString`视图或`CString`控件视图对象中组合框控件的编辑控件与对话框、窗体视图或控件视图对象的数据成员之间的数据传输。 `DDX_CBStringExact`

```
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的组合框控件的资源 ID。

*value*<br/>
对用于交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

调用`DDX_CBStringExact`时， *value*设置为当前组合框选择。 如果未选择任何项，则将*值*设置为长度为零的字符串。

> [!NOTE]
>  如果组合框为下拉列表框，则交换的值限制为255个字符。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

##  <a name="ddx_check"></a>  DDX_Check

函数管理对话框、窗体视图或控件视图对象中的复选框控件与对话框、窗体视图或控件视图对象的**int**数据成员之间的 int 数据的传输。 `DDX_Check`

```
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的复选框控件的资源 ID。

*value*<br/>
对用于交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

调用`DDX_Check`时， *value*设置为复选框控件的当前状态。 有关可能状态值的列表，请参阅 Windows SDK 中的[BM_GETCHECK](/windows/win32/Controls/bm-getcheck) 。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

##  <a name="ddx_control"></a>  DDX_Control

该`DDX_Control`函数对由对话框、窗体视图或控件视图对象的*nIDC*指定的控件进行子类控制。

```
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

*nIDC*<br/>
要进行细分的控件的资源 ID。

*rControl*<br/>
对与指定控件相关的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

调用 `DoDataExchange`函数时，pDX 对象由框架提供。 因此， `DDX_Control`只应在`DoDataExchange`重写中调用。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

##  <a name="ddx_datetimectrl"></a>  DDX_DateTimeCtrl

`DDX_DateTimeCtrl`函数管理对话框或窗体视图对象中日期和时间选择器控件（ [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)）与对话框或窗体的[CTime](../../atl-mfc-shared/reference/ctime-class.md)或 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 数据成员之间的日期和/或时间数据的传输 视图对象。

```
void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    CTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。 不需要删除此对象。

*nIDC*<br/>
与成员变量关联的日期和时间选择器控件的资源 ID。

*value*<br/>
在前两个版本中，是指对`CTime`与其`COleDateTime`交换数据的或成员变量、对话框、窗体视图或控件视图对象的引用。 在第三个版本中，是对`CString`数据成员控件视图对象的引用。

### <a name="remarks"></a>备注

调用`DDX_DateTimeCtrl`时，将*value*设置为日期和时间选择器控件的当前状态，或将控件设置为*值*，具体取决于交换的方向。

在上述第三个版本`DDX_DateTimeCtrl`中，管理日期`CString`时间控件和控件视图对象的[CString](../../atl-mfc-shared/reference/cstringt-class.md)数据成员之间的数据传输。 使用当前区域设置的日期和时间格式规则对字符串进行格式设置。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

## <a name="ddx_managedcontrol"></a>DDX_ManagedControl

创建与控件的资源 ID 相匹配的 .NET 控件。

### <a name="syntax"></a>语法

```
template <typename T>
void DDX_ManagedControl(
   CDataExchange* pDX,
   int nIDC,
   CWinFormsControl<T>& control );
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange 类](cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的控件的资源 ID。

*control*<br/>
对[CWinFormsControl 类](cwinformscontrol-class.md)对象的引用。

### <a name="remarks"></a>备注

`DDX_ManagedControl`调用[CWinFormsControl：： CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)以创建一个与资源控件 ID 相匹配的控件。 使用`DDX_ManagedControl`从[CDialog：： OnInitDialog](cdialog-class.md#oninitdialog)中的资源 id 创建控件。 对于数据交换，无需将 DDX/DDV 函数用于 Windows 窗体控件。

有关详细信息，请参阅[如何：执行 DDX/DDV 数据绑定与 Windows 窗体](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)。

### <a name="requirements"></a>要求

**标头：** afxwinforms

##  <a name="ddx_ipaddress"></a>  DDX_IPAddress

`DDX_IPAddress`函数管理 IP 地址控件和控件视图对象的数据成员之间的数据传输。

```
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的 IP 地址控件的资源 ID。

*value*<br/>
对包含 IP 地址控件的四个字段值的 DWORD 值的引用。 按如下所示填充或读取字段。

|字段|包含字段值的位|
|-----------|-------------------------------------|
|3|0到7|
|2|8到15|
|1|16到23|
|0|24到31|

使用 Win32 [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress)读取值，或使用[IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress)填充值。 Windows SDK 中介绍了这些消息。

### <a name="remarks"></a>备注

调用`DDX_IPAddress`时，将从 IP 地址控件中读取*值*，或者将*值*写入控件，具体取决于交换的方向。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

##  <a name="ddx_lbindex"></a>  DDX_LBIndex

函数管理对话框、窗体视图或控件视图对象中的列表框控件与对话框、窗体视图或控件视图对象的**int**数据成员之间的 int 数据的传输。 `DDX_LBIndex`

```
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的列表框控件的资源 ID。

*index*<br/>
对用于交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

调用`DDX_LBIndex`时， *index*设置为当前列表框选择的索引。 如果未选择任何项，则*index*设置为-1。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

##  <a name="ddx_lbstring"></a>  DDX_LBString

函数管理对话框、窗体`CString`视图或`CString`控件视图对象中的列表框控件与对话框、窗体视图或控件视图对象的数据成员之间的数据传输。 `DDX_LBString`

```
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的列表框控件的资源 ID。

*value*<br/>
对用于交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

调用`DDX_LBString`以将数据传输到列表框控件时，将选择控件中其开头匹配*值*的第一项。 （若要匹配整个项而不只是一个前缀，请使用[DDX_LBStringExact](#ddx_lbstringexact)。）如果没有匹配项，则不选择任何项。 匹配不区分大小写。

在`DDX_LBString`调用以从列表框控件传输数据时，将*值*设置为当前列表框选择。 如果未选择任何项，则将*值*设置为长度为零的字符串。

> [!NOTE]
>  如果列表框为下拉列表框，则交换的值限制为255个字符。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

##  <a name="ddx_lbstringexact"></a>  DDX_LBStringExact

函数管理对话框、窗体`CString`视图或`CString`控件视图对象的编辑控件与对话框、窗体视图或控件视图对象的数据成员之间的数据传输。 `DDX_CBStringExact`

```
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的列表框控件的资源 ID。

*value*<br/>
对用于交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

调用`DDX_LBStringExact`以将数据传输到列表框控件时，将选择控件中与*值*匹配的第一项。 （若要只匹配前缀而不是整个项目，请使用[DDX_LBString](#ddx_lbstring)。）如果没有匹配项，则不选择任何项。 匹配不区分大小写。

在`DDX_CBStringExact`调用以从列表框控件传输数据时，将*值*设置为当前列表框选择。 如果未选择任何项，则将*值*设置为长度为零的字符串。

> [!NOTE]
>  如果列表框为下拉列表框，则交换的值限制为255个字符。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

##  <a name="ddx_monthcalctrl"></a>  DDX_MonthCalCtrl

`DDX_MonthCalCtrl`函数管理对话框、窗体视图或控件视图对象中的月历控件（ [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)）之间的日期数据传输，以及对话框的[CTime](../../atl-mfc-shared/reference/ctime-class.md)或 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 数据成员窗体 视图或控件视图对象。

```
void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,
    int nIDC,
    CTime& value);

void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。 不需要删除此对象。

*nIDC*<br/>
与成员变量关联的月历控件的资源 ID。

*value*<br/>
对用于交换数据`CTime`的`COleDateTime`对话框、窗体视图或控件视图对象的或成员变量的引用。

### <a name="remarks"></a>备注

> [!NOTE]
>  控件仅管理日期值。 Time 对象中的时间字段设置为反映控件窗口的创建时间，或在控件中通过调用`CMonthCalCtrl::SetCurSel`设置的任何时间。

调用`DDX_MonthCalCtrl`时， *value*设置为月历控件的当前状态。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

##  <a name="ddx_radio"></a>DDX_Radio

函数管理对话框、窗体视图或控件视图对象中的单选控件组与对话框、窗体视图或控件视图对象的**int**数据成员之间的 int 数据的传输。 `DDX_Radio` **Int**数据成员的值根据组中选定的单选按钮来确定。

```
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
组中第一个单选控件的资源 ID。

*value*<br/>
对用于交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

调用`DDX_Radio`时， *value*设置为单选按钮组的当前状态。 此值设置为当前选中的单选控件的从零开始的索引; 如果没有选中任何广播控件，则为-1。

例如，如果检查组中的第一个单选按钮（带有 WS_GROUP 样式的按钮），则**int**成员的值为0，依此类推。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

##  <a name="ddx_scroll"></a>  DDX_Scroll

函数管理对话框、窗体视图或控件视图对象中滚动条控件与对话框、窗体视图或控件视图对象的**int**数据成员之间的 int 数据的传输。 `DDX_Scroll`

```
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的滚动条控件的资源 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

调用`DDX_Scroll`时， *value*设置为控件的滚动块的当前位置。 有关与控件的滚动块当前位置关联的值的详细信息，请参阅 Windows SDK 中的[GetScrollPos](/windows/win32/api/winuser/nf-winuser-getscrollpos) 。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

##  <a name="ddx_slider"></a>  DDX_Slider

函数管理对话框或窗体视图中滑块控件与对话框或窗体视图对象的**int**数据成员之间的 int 数据的传输。 `DDX_Slider`

```
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
滑块控件的资源 ID。

*value*<br/>
对要交换的值的引用。 此参数包含或设置滑块控件的当前位置。

### <a name="remarks"></a>备注

当`DDX_Slider`调用时， *value*设置为控件 thumb 的当前位置，或该值接收位置，具体取决于交换的方向。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关滑块控件的信息，请参阅[Using CSliderCtrl](../../mfc/using-csliderctrl.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

##  <a name="ddx_text"></a>DDX_Text

`DDX_Text`      函数管理对话框、窗体视图或控件视图中的编辑控件与 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 数据之间的 int、UINT、long、DWORD、`CString`、float 或 double 数据的传输对话框、窗体视图或控件视图对象的成员。

```
void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    short& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    int& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    UINT& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    long& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    CString& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    float& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    double& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
对话框、窗体视图或控件视图对象中编辑控件的 ID。

*value*<br/>
对对话框、窗体视图或控件视图对象中的数据成员的引用。 *值*的数据类型取决于使用的重载版本`DDX_Text`中的哪一种。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_

## <a name="see-also"></a>请参阅

[标准对话框数据验证例程](standard-dialog-data-validation-routines.md)<br/>
[宏和全局](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
