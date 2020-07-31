---
title: OLE 控件的对话框数据交换函数
ms.date: 11/04/2016
f1_keywords:
- AFXDISP/DDX_OCBool
- AFXDISP/DDX_OCBoolRO
- AFXDISP/DDX_OCColor
- AFXDISP/DDX_OCColorRO
- AFXDISP/DDX_OCFloat
- AFXDISP/DDX_OCFloatRO
- AFXDISP/DDX_OCInt
- AFXDISP/DDX_OCIntRO
- AFXDISP/DDX_OCShort
- AFXDISP/DDX_OCShortRO
- AFXDISP/DDX_OCText
- AFXDISP/DDX_OCTextRO
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
ms.openlocfilehash: b5a7263ae5cac81508ab2450a530132879ed45b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222818"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>OLE 控件的对话框数据交换函数

本主题列出了用于在对话框、窗体视图或控件视图对象的属性与对话框、窗体视图或控件视图对象的数据成员之间交换数据的 DDX_OC 函数。

### <a name="ddx_oc-functions"></a>DDX_OC 函数

|||
|-|-|
|[DDX_OCBool](#ddx_ocbool)|管理 OLE 控件的属性和**bool**数据成员之间的**布尔**数据传输。|
|[DDX_OCBoolRO](#ddx_ocboolro)|管理在 OLE 控件和**bool**数据成员的只读属性之间传输的**布尔**数据。|
|[DDX_OCColor](#ddx_occolor)|管理 OLE 控件的属性和**OLE_COLOR**数据成员之间**OLE_COLOR**数据的传输。|
|[DDX_OCColorRO](#ddx_occolorro)|管理 OLE 控件的只读属性与**OLE_COLOR**数据成员之间**OLE_COLOR**数据的传输。|
|[DDX_OCFloat](#ddx_ocfloat)|管理 **`float`** **`double`** OLE 控件的属性和 **`float`** （或 **`double`** ）数据成员之间的数据传输（或）。|
|[DDX_OCFloatRO](#ddx_ocfloatro)|管理 **`float`** **`double`** OLE 控件的只读属性与 **`float`** （或 **`double`** ）数据成员之间的数据传输（或）。|
|[DDX_OCInt](#ddx_ocint)|管理 **`int`** **`long`** OLE 控件的属性和 **`int`** （或 **`long`** ）数据成员之间的数据传输（或）。|
|[DDX_OCIntRO](#ddx_ocintro)|管理 **`int`** **`long`** OLE 控件的只读属性与 **`int`** （或 **`long`** ）数据成员之间的数据传输（或）。|
|[DDX_OCShort](#ddx_ocshort)|管理 **`short`** OLE 控件的属性和数据成员之间的数据传输 **`short`** 。|
|[DDX_OCShortRO](#ddx_ocshortro)|管理 **`short`** OLE 控件的只读属性与数据成员之间的数据传输 **`short`** 。|
|[DDX_OCText](#ddx_octext)|管理 OLE 控件的属性和**cstring**数据成员之间**CString**数据的传输。|
|[DDX_OCTextRO](#ddx_octextro)|管理在 OLE 控件和**CString**数据成员的只读属性之间传输**CString**数据的情况。|

## <a name="ddx_ocbool"></a><a name="ddx_ocbool"></a>DDX_OCBool

`DDX_OCBool`函数管理对话框、窗体视图或控件视图对象中 OLE 控件的属性与对话框、窗体视图或控件视图对象的**布尔**数据成员之间的**bool**数据传输。

```cpp
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
对话框、窗体视图或控件视图对象中 OLE 控件的 ID。

*dispid*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头：** afxdisp.h

## <a name="ddx_ocboolro"></a><a name="ddx_ocboolro"></a>DDX_OCBoolRO

`DDX_OCBoolRO`函数管理对话框、窗体视图或控件视图对象中 OLE 控件的只读属性与对话框、窗体视图或控件视图对象的**布尔**数据成员之间的**布尔**数据的传输。

```cpp
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
对话框、窗体视图或控件视图对象中 OLE 控件的 ID。

*dispid*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdisp.h&gt

## <a name="ddx_occolor"></a><a name="ddx_occolor"></a>DDX_OCColor

`DDX_OCColor`函数管理对话框、窗体视图或控件视图对象中 OLE 控件的属性与对话框、窗体视图或控件视图对象 OLE_COLOR 数据成员之间 OLE_COLOR 数据的传输。

```cpp
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
对话框、窗体视图或控件视图对象中 OLE 控件的 ID。

*dispid*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdisp.h&gt

## <a name="ddx_occolorro"></a><a name="ddx_occolorro"></a>DDX_OCColorRO

`DDX_OCColorRO`函数管理对话框、窗体视图或控件视图对象中 OLE 控件的只读属性与对话框、窗体视图或控件视图对象 OLE_COLOR 数据成员之间 OLE_COLOR 数据的传输。

```cpp
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
对话框、窗体视图或控件视图对象中 OLE 控件的 ID。

*dispid*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdisp.h&gt

## <a name="ddx_ocfloat"></a><a name="ddx_ocfloat"></a>DDX_OCFloat

`DDX_OCFloat`函数管理 **`float`** **`double`** 对话框、窗体视图或控件视图对象中 OLE 控件的属性与 **`float`** **`double`** 对话框、窗体视图或控件视图对象的（或）数据成员之间的数据传输。

```cpp
void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
对话框、窗体视图或控件视图对象中 OLE 控件的 ID。

*dispid*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdisp.h&gt

## <a name="ddx_ocfloatro"></a><a name="ddx_ocfloatro"></a>DDX_OCFloatRO

`DDX_OCFloatRO`函数管理 **`float`** **`double`** 对话框、窗体视图或控件视图对象中 OLE 控件的只读属性与 **`float`** **`double`** 对话框、窗体视图或控件视图对象的（或）数据成员之间的数据传输。

```cpp
void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
对话框、窗体视图或控件视图对象中 OLE 控件的 ID。

*dispid*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdisp.h&gt

## <a name="ddx_ocint"></a><a name="ddx_ocint"></a>DDX_OCInt

`DDX_OCInt`函数管理 **`int`** **`long`** 对话框、窗体视图或控件视图对象中 OLE 控件的属性与 **`int`** **`long`** 对话框、窗体视图或控件视图对象的（或）数据成员之间的数据传输。

```cpp
void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
对话框、窗体视图或控件视图对象中 OLE 控件的 ID。

*dispid*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdisp.h&gt

## <a name="ddx_ocintro"></a><a name="ddx_ocintro"></a>DDX_OCIntRO

`DDX_OCIntRO`函数管理 **`int`** **`long`** 对话框、窗体视图或控件视图对象中 OLE 控件的只读属性与 **`int`** **`long`** 对话框、窗体视图或控件视图对象的（或）数据成员之间的数据传输。

```cpp
void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
对话框、窗体视图或控件视图对象中 OLE 控件的 ID。

*dispid*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdisp.h&gt

## <a name="ddx_ocshort"></a><a name="ddx_ocshort"></a>DDX_OCShort

`DDX_OCShort`函数管理对话框、窗体视图或控件视图对象中 OLE 控件的属性与对话框、窗体视图或控件视图对象的简短数据成员之间的短数据传输。

```cpp
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
对话框、窗体视图或控件视图对象中 OLE 控件的 ID。

*dispid*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdisp.h&gt

## <a name="ddx_ocshortro"></a><a name="ddx_ocshortro"></a>DDX_OCShortRO

`DDX_OCShortRO`函数管理对话框、窗体视图或控件视图对象中 OLE 控件的只读属性与对话框、窗体视图或控件视图对象的简短数据成员之间的短数据传输。

```cpp
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
对话框、窗体视图或控件视图对象中 OLE 控件的 ID。

*dispid*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdisp.h&gt

## <a name="ddx_octext"></a><a name="ddx_octext"></a>DDX_OCText

**DDX_OCText**函数管理对话框、窗体视图或控件视图对象中 OLE 控件的属性与对话框、窗体视图或控件视图对象的**CString**数据成员之间的**cstring**数据的传输。

```cpp
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向**CDataExchange**对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
对话框、窗体视图或控件视图对象中 OLE 控件的 ID。

*dispid*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdisp.h&gt

## <a name="ddx_octextro"></a><a name="ddx_octextro"></a>DDX_OCTextRO

`DDX_OCTextRO` 函数管理对话框、窗体视图或控件视图对象中 OLE 控件的只读属性与对话框、窗体视图或控件视图对象的 `CString` 数据成员之间 `CString` 数据的传输。

```cpp
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*nIDC*<br/>
对话框、窗体视图或控件视图对象中 OLE 控件的 ID。

*dispid*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdisp.h&gt

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
