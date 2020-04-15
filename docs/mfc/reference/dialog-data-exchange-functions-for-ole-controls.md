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
ms.openlocfilehash: 61a5983eec13902ed4b0e397e3befca4860977d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365765"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>OLE 控件的对话框数据交换函数

本主题列出了用于在对话框、窗体视图或控件视图对象中的 OLE 控件的属性与对话框、窗体视图或控件视图对象的数据成员之间交换数据的DDX_OC函数。

### <a name="ddx_oc-functions"></a>DDX_OC功能

|||
|-|-|
|[DDX_OCBool](#ddx_ocbool)|管理**BOOL**数据在 OLE 控件的属性和**BOOL**数据成员之间的传输。|
|[DDX_OCBoolRO](#ddx_ocboolro)|管理**BOOL**数据在 OLE 控件的只读属性和**BOOL**数据成员之间的传输。|
|[DDX_OCColor](#ddx_occolor)|管理**OLE_COLOR**数据在 OLE 控件的属性和**OLE_COLOR**数据成员之间的传输。|
|[DDX_OCColorRO](#ddx_occolorro)|管理**OLE_COLOR**的 OLE 控件的只读属性和**OLE_COLOR**数据成员之间的传输。|
|[DDX_OCFloat](#ddx_ocfloat)|管理 OLE 控件的属性和**浮点**（或**双**精度）数据成员之间的**浮点**（或**双精度**）数据传输。|
|[DDX_OCFloatRO](#ddx_ocfloatro)|管理 OLE 控件的只读属性和**浮点**（或**双****精度**）数据成员之间的**浮点**（或双精度）数据传输。|
|[DDX_OCInt](#ddx_ocint)|管理在 OLE 控件的属性和**long** **int（** 或长）数据成员之间传输**int（** 或**长**） 数据。|
|[DDX_OCIntRO](#ddx_ocintro)|管理在 OLE 控件的只**long**读属性和**int（** 或长）数据成员之间传输**int（** 或**长**） 数据。|
|[DDX_OCShort](#ddx_ocshort)|管理 OLE 控件的属性和**短**数据成员之间的**短**数据传输。|
|[DDX_OCShortRO](#ddx_ocshortro)|管理 OLE 控件的只读属性和**短**数据成员之间的**短**数据传输。|
|[DDX_OCText](#ddx_octext)|管理在 OLE 控件的属性和**CString**数据成员之间传输**CString**数据。|
|[DDX_OCTextRO](#ddx_octextro)|管理在 OLE 控件的只读属性和**CString**数据成员之间传输**CString**数据。|

## <a name="ddx_ocbool"></a><a name="ddx_ocbool"></a>DDX_OCBool

该`DDX_OCBool`函数管理**在**对话框、窗体视图或控件视图对象中的 OLE 控件的属性与对话框、窗体视图或控件视图对象的**BOOL**数据成员之间的传输。

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

*不一部分*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头：** afxdisp.h

## <a name="ddx_ocboolro"></a><a name="ddx_ocboolro"></a>DDX_OCBoolRO

该`DDX_OCBoolRO`函数管理**在**对话框、窗体视图或控件视图对象中的 OLE 控件的只读属性和对话框、窗体视图或控件视图对象的**BOOL**数据成员之间的传输。

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

*不一部分*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="ddx_occolor"></a><a name="ddx_occolor"></a>DDX_OCColor

该`DDX_OCColor`函数管理在对话框、窗体视图或控件视图对象中的 OLE 控件的属性与对话框、窗体视图或控件视图对象的OLE_COLOR数据成员之间的传输OLE_COLOR数据。

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

*不一部分*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="ddx_occolorro"></a><a name="ddx_occolorro"></a>DDX_OCColorRO

该`DDX_OCColorRO`函数管理在对话框、窗体视图或控件视图对象的仅读属性和对话框、窗体视图或控件视图对象的OLE_COLOR数据成员之间的传输OLE_COLOR数据。

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

*不一部分*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="ddx_ocfloat"></a><a name="ddx_ocfloat"></a>DDX_OCFloat

该`DDX_OCFloat`函数管理在对话框、窗体视图或控件视图对象的 OLE 控件的属性和对话框、窗体视图或控件视图对象的**浮点**（或**双**）数据成员之间的**浮动**（或**双**）数据之间的传输。

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

*不一部分*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="ddx_ocfloatro"></a><a name="ddx_ocfloatro"></a>DDX_OCFloatRO

该`DDX_OCFloatRO`函数管理在对话框、窗体视图或控件视图对象中的 OLE 控件的只读属性和对话框、窗体视图或控件视图对象的**浮点**（或**双**）数据成员之间的**浮动**（或**双**）数据之间的传输。

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

*不一部分*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="ddx_ocint"></a><a name="ddx_ocint"></a>DDX_OCInt

该`DDX_OCInt`函数管理在对话框、窗体视图或控件视图对象中的 OLE 控件的属性与对话框、窗体视图或控件视图对象的**int（** 或**长**）数据成员之间的**int（** 或**长**） 数据之间的传输。

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

*不一部分*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="ddx_ocintro"></a><a name="ddx_ocintro"></a>DDX_OCIntRO

该`DDX_OCIntRO`函数管理在对话框、窗体视图或控件视图对象中的 OLE 控件的只读属性和对话框、窗体视图或控件视图对象的**int（** 或**长**）数据成员之间的**int（** 或**长**） 数据的传输。

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

*不一部分*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="ddx_ocshort"></a><a name="ddx_ocshort"></a>DDX_OCShort

该`DDX_OCShort`函数管理在对话框、窗体视图或控件视图对象中的 OLE 控件的属性与对话框、窗体视图或控件视图对象的短数据成员之间的短数据传输。

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

*不一部分*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="ddx_ocshortro"></a><a name="ddx_ocshortro"></a>DDX_OCShortRO

该`DDX_OCShortRO`函数管理在对话框、窗体视图或控件视图对象中的 OLE 控件的只读属性和对话框、窗体视图或控件视图对象的短数据成员之间的短数据传输。

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

*不一部分*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="ddx_octext"></a><a name="ddx_octext"></a>DDX_OCText

**DDX_OCText**函数管理**在**对话框、窗体视图或控件视图对象中的 OLE 控件的属性与对话框、窗体视图或控件视图对象的 CString 数据成员之间的**CString**数据传输。

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

*不一部分*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

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

*不一部分*<br/>
该控件的属性的调度 ID。

*value*<br/>
对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。

### <a name="remarks"></a>备注

有关 DDX 的更多信息，请参阅 [对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdisp.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
