---
title: 标准对话框数据交换例程
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 83d4a66cd3ec41008506b55f0b351fd9bcbc24b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372935"
---
# <a name="standard-dialog-data-exchange-routines"></a>标准对话框数据交换例程

本主题列出了用于常见 MFC 对话框控件的标准对话框数据交换 （DDX） 例程。

> [!NOTE]
> 标准对话框数据交换例程在标头文件 afxdd_.h 中定义。 但是，应用程序应包括 afxwin.h。

### <a name="ddx-functions"></a>DDX 功能

|||
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|初始化或检索组合框控件的当前选择的索引。|
|[DDX_CBString](#ddx_cbstring)|初始化或检索组合框控件的编辑字段的当前内容。|
|[DDX_CBStringExact](#ddx_cbstringexact)|初始化或检索组合框控件的编辑字段的当前内容。|
|[DDX_Check](#ddx_check)|初始化或检索复选框控件的当前状态。|
|[DDX_Control](#ddx_control)|在对话框中对给定控件进行子类。|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|初始化或检索日期和时间选取器控件的日期和/或时间数据。|
|[DDX_IPAddress](#ddx_ipaddress)|初始化或检索 IP 地址控件的当前值。|
|[DDX_LBIndex](#ddx_lbindex)|初始化或检索列表框控件的当前选择的索引。|
|[DDX_LBString](#ddx_lbstring)|在列表框控件中初始化或检索当前选择。|
|[DDX_LBStringExact](#ddx_lbstringexact)|在列表框控件中初始化或检索当前选择。|
|[DDX_ManagedControl](#ddx_managedcontrol)|创建与控件的资源 ID 匹配的 .NET 控件。|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|初始化或检索月份日历控件的当前值。|
|[DDX_Radio](#ddx_radio)|初始化或检索当前在无线电控制组中检查的无线电控件的 0 个基于 0 的索引。|
|[DDX_Scroll](#ddx_scroll)|初始化或检索滚动控件拇指的当前位置。|
|[DDX_Slider](#ddx_slider)|初始化或检索滑块控件拇指的当前位置。|
|[DDX_Text](#ddx_text)|初始化或检索编辑控件的当前值。|

## <a name="ddx_cbindex"></a><a name="ddx_cbindex"></a>DDX_CBIndex

该`DDX_CBIndex`函数管理在对话框、窗体视图或控件视图对象中的组合框控件和对话框、窗体视图或控件视图对象的**int**数据成员之间的**int**数据传输。

```cpp
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的组合框控件的资源 ID。

*index*<br/>
对对话框、窗体视图或控件视图对象的成员变量的引用，用于交换数据。

### <a name="remarks"></a>备注

调用`DDX_CBIndex`时，*索引*将设置为当前组合框选择的索引。 如果未选择任何项，*则索引*设置为 0。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddx_cbstring"></a><a name="ddx_cbstring"></a>DDX_CBString

该`DDX_CBString`函数管理对话框、窗体`CString`视图或控件视图对象组合框控件的编辑控件与对话框、窗体视图或控件视图对象`CString`的数据成员之间的数据传输。

```cpp
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的组合框控件的资源 ID。

*value*<br/>
对对话框、窗体视图或控件视图对象的成员变量的引用，用于交换数据。

### <a name="remarks"></a>备注

调用`DDX_CBString`时，*值*设置为当前组合框选择。 如果未选择任何项，*则值*将设置为长度为零的字符串。

> [!NOTE]
> 如果组合框是下拉列表框，则交换的值限制为 255 个字符。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddx_cbstringexact"></a><a name="ddx_cbstringexact"></a>DDX_CBStringExact

该`DDX_CBStringExact`函数管理对话框、窗体`CString`视图或控件视图对象组合框控件的编辑控件与对话框、窗体视图或控件视图对象`CString`的数据成员之间的数据传输。

```cpp
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的组合框控件的资源 ID。

*value*<br/>
对对话框、窗体视图或控件视图对象的成员变量的引用，用于交换数据。

### <a name="remarks"></a>备注

调用`DDX_CBStringExact`时，*值*设置为当前组合框选择。 如果未选择任何项，*则值*将设置为长度为零的字符串。

> [!NOTE]
> 如果组合框是下拉列表框，则交换的值限制为 255 个字符。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddx_check"></a><a name="ddx_check"></a>DDX_Check

该`DDX_Check`函数管理在对话框、窗体视图或控件视图对象的复选框控件和对话框、窗体视图或控件视图对象的**int**数据成员之间传输**int**数据。

```cpp
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的复选框控件的资源 ID。

*value*<br/>
对对话框、窗体视图或控件视图对象的成员变量的引用，用于交换数据。

### <a name="remarks"></a>备注

调用`DDX_Check`时，*值*设置为复选框控件的当前状态。 有关可能的状态值的列表，请参阅 Windows SDK 中的[BM_GETCHECK。](/windows/win32/Controls/bm-getcheck)

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddx_control"></a><a name="ddx_control"></a>DDX_Control

函数`DDX_Control`对对话框、窗体视图或控件视图对象的控件进行子类，由*nIDC*指定。

```cpp
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。

*nIDC*<br/>
要子类的控件的资源 ID。

*r控制*<br/>
对对话框、窗体视图或控件视图对象的成员变量的引用，该变量与指定的控件相关。

### <a name="remarks"></a>备注

当调用`DoDataExchange`函数时 *，pDX*对象由框架提供。 因此，`DDX_Control`只能在 对 的`DoDataExchange`重写中调用 。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddx_datetimectrl"></a><a name="ddx_datetimectrl"></a>DDX_DateTimeCtrl

该`DDX_DateTimeCtrl`函数管理日期和时间选取器控件[（CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)） 在对话框或窗体视图对象以及对话框或窗体视图对象的[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)数据成员之间的日期和/或时间数据的传输。

```cpp
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
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。 您无需删除此对象。

*nIDC*<br/>
与成员变量关联的日期和时间选取器控件的资源 ID。

*value*<br/>
在前两个版本中，对交换数据的或`CTime``COleDateTime`成员变量、对话框、窗体视图或控件视图对象的引用。 在第三个版本中，对`CString`数据成员控件视图对象的引用。

### <a name="remarks"></a>备注

调用`DDX_DateTimeCtrl`时，*值*设置为日期和时间选取器控件的当前状态，或者控件设置为*值*，具体取决于交换的方向。

在上面的第三个版本中，`DDX_DateTimeCtrl`管理日期时间控件`CString`和控制视图对象的[CString](../../atl-mfc-shared/reference/cstringt-class.md)数据成员之间的数据传输。 字符串使用当前区域设置的规则格式化日期和时间。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddx_managedcontrol"></a><a name="ddx_managedcontrol"></a>DDX_ManagedControl

创建与控件的资源 ID 匹配的 .NET 控件。

### <a name="syntax"></a>语法

```cpp
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

*控制*<br/>
对[CWinForms 控制类](cwinformscontrol-class.md)对象的引用。

### <a name="remarks"></a>备注

`DDX_ManagedControl`调用[CWinForms 控制：：创建托管控制](cwinformscontrol-class.md#createmanagedcontrol)以创建与资源控制 ID 匹配的控件。 用于`DDX_ManagedControl`在 CDialog 中从资源 ID 创建控件[：onInitDialog](cdialog-class.md#oninitdialog)。 对于数据交换，您无需将 DDX/DDV 函数与 Windows 窗体控件一起使用。

有关详细信息，请参阅[如何：使用 Windows 窗体 进行 DDX/DDV 数据绑定](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)。

### <a name="requirements"></a>要求

**标题：** afxwinforms.h

## <a name="ddx_ipaddress"></a><a name="ddx_ipaddress"></a>DDX_IPAddress

该`DDX_IPAddress`函数管理 IP 地址控件和控制视图对象的数据成员之间的数据传输。

```cpp
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的 IP 地址控件的资源 ID。

*value*<br/>
对包含 IP 地址控件的四字段值的 DWORD 的引用。 字段填充或读取如下。

|字段|包含字段值的位|
|-----------|-------------------------------------|
|3|0 到 7|
|2|8 到 15|
|1|16 到 23|
|0|24 到 31|

使用 Win32 [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress)读取该值，或使用[IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress)填充该值。 这些消息在 Windows SDK 中描述。

### <a name="remarks"></a>备注

调用`DDX_IPAddress`时，*值*要么从 IP 地址控件读取 *，要么根据*交换的方向写入控件。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddx_lbindex"></a><a name="ddx_lbindex"></a>DDX_LBIndex

该`DDX_LBIndex`函数管理在对话框、窗体视图或控件视图对象中的列表框控件和对话框、窗体视图或控件视图对象的**int**数据成员之间的**int**数据传输。

```cpp
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的列表框控件的资源 ID。

*index*<br/>
对对话框、窗体视图或控件视图对象的成员变量的引用，用于交换数据。

### <a name="remarks"></a>备注

调用`DDX_LBIndex`时，*索引*将设置为当前列表框选择的索引。 如果未选择任何项，*则索引*设置为 -1。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddx_lbstring"></a><a name="ddx_lbstring"></a>DDX_LBString

该`DDX_LBString`函数管理对话框、窗体`CString`视图或控件视图对象中的列表框控件与对话框、窗体视图或控件视图对象`CString`的数据成员之间的数据传输。

```cpp
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的列表框控件的资源 ID。

*value*<br/>
对对话框、窗体视图或控件视图对象的成员变量的引用，用于交换数据。

### <a name="remarks"></a>备注

当`DDX_LBString`调用将数据传输到列表框控件时，将选择其开始匹配*值*的控件中的第一个项。 （要匹配整个项目，而不仅仅是前缀，请使用[DDX_LBStringExact](#ddx_lbstringexact)。如果没有匹配项，则不选择任何项目。 匹配不区分大小写。

当`DDX_LBString`调用从列表框控件传输数据时，*值*将设置为当前列表框选择。 如果未选择任何项，*则值*将设置为长度为零的字符串。

> [!NOTE]
> 如果列表框是下拉列表框，则交换的值限制为 255 个字符。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddx_lbstringexact"></a><a name="ddx_lbstringexact"></a>DDX_LBStringExact

该`DDX_CBStringExact`函数管理对话框、窗体`CString`视图或控件视图对象中列表框控件的编辑控件与对话框、窗体视图或控件视图对象`CString`的数据成员之间的数据传输。

```cpp
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的列表框控件的资源 ID。

*value*<br/>
对对话框、窗体视图或控件视图对象的成员变量的引用，用于交换数据。

### <a name="remarks"></a>备注

当`DDX_LBStringExact`调用将数据传输到列表框控件时，将选择控件中与*值*匹配的第一项。 （要仅匹配前缀而不是整个项目，请使用[DDX_LBString](#ddx_lbstring)。如果没有匹配项，则不选择任何项目。 匹配不区分大小写。

当`DDX_CBStringExact`调用从列表框控件传输数据时，*值*将设置为当前列表框选择。 如果未选择任何项，*则值*将设置为长度为零的字符串。

> [!NOTE]
> 如果列表框是下拉列表框，则交换的值限制为 255 个字符。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddx_monthcalctrl"></a><a name="ddx_monthcalctrl"></a>DDX_MonthCalCtrl

该`DDX_MonthCalCtrl`函数管理在对话框、窗体视图或控件视图对象以及对话框[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)、窗体视图或控件视图对象的[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)数据成员之间的日期数据传输。

```cpp
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
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。 您无需删除此对象。

*nIDC*<br/>
与成员变量关联的月份日历控件的资源 ID。

*value*<br/>
对对话框、窗体`CTime`视图`COleDateTime`或控件视图对象的 或 成员变量的引用，用于交换数据。

### <a name="remarks"></a>备注

> [!NOTE]
> 控件仅管理日期值。 时间对象中的时间字段设置为反映控件窗口的创建时间，或者控件中设置的任何时间以及调用`CMonthCalCtrl::SetCurSel`。

调用`DDX_MonthCalCtrl`时，*值*设置为月历控件的当前状态。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddx_radio"></a><a name="ddx_radio"></a>DDX_Radio

该`DDX_Radio`函数管理在对话框、窗体视图或控件视图对象中的无线电控制组和对话框、窗体视图或控件视图对象的**int**数据成员之间的**int**数据传输。 **int**数据成员的值根据组中的哪个单选按钮确定。

```cpp
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
组中第一个无线电控件的资源 ID。

*value*<br/>
对对话框、窗体视图或控件视图对象的成员变量的引用，用于交换数据。

### <a name="remarks"></a>备注

调用`DDX_Radio`时，*值*设置为无线电控制组的当前状态。 该值设置为当前检查的无线电控件的 0 个索引，如果未检查无线电控件，则设置为 -1。

例如，如果选中组中的第一个单选按钮（具有WS_GROUP样式的按钮 **），int**成员的值为 0，等等。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddx_scroll"></a><a name="ddx_scroll"></a>DDX_Scroll

该`DDX_Scroll`函数管理在对话框、窗体视图或控件视图对象中的滚动条控件和对话框、窗体视图或控件视图对象的**int**数据成员之间的**int**数据传输。

```cpp
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
与控件属性关联的滚动条控件的资源 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

调用`DDX_Scroll`时，*值*设置为控件拇指的当前位置。 有关与控件的拇指当前位置关联的值的详细信息，请参阅 Windows SDK 中的[GetScrollPos。](/windows/win32/api/winuser/nf-winuser-getscrollpos)

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddx_slider"></a><a name="ddx_slider"></a>DDX_Slider

该`DDX_Slider`函数管理在对话框或窗体视图中的滑块控件和对话框或窗体视图对象的**int**数据成员之间的**int**数据传输。

```cpp
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
对要交换的值的引用。 此参数保留或设置滑块控件的当前位置。

### <a name="remarks"></a>备注

调用`DDX_Slider`时，*值*设置为控件拇指的当前位置，或者该值接收位置，具体取决于交换的方向。

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关滑块控件的信息，请参阅[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddx_text"></a><a name="ddx_text"></a>DDX_Text

该`DDX_Text`函数管理在对话框、窗体视图或控件视图的编辑控件**long**和对话框、窗体视图`CString`或控件视图对象的[CString](../../atl-mfc-shared/reference/cstringt-class.md)数据成员之间的 int、UINT、长、DWORD、float 或**双数据**之间的传输。 **int** **UINT** **float**

```cpp
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
对对话框、窗体视图或控件视图对象中的数据成员的引用。 *值*的数据类型取决于`DDX_Text`您使用的重载版本。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="see-also"></a>另请参阅

[标准对话框数据验证例程](standard-dialog-data-validation-routines.md)<br/>
[MFC 宏和全局函数](mfc-macros-and-globals.md)<br/>
[CWinForms控制：创建托管控制](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog：onInitDialog](cdialog-class.md#oninitdialog)
