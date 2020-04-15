---
title: 标准对话框数据验证例程
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 83e3e215ec8d66321bbac5a4a308b04ef69dc68c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372901"
---
# <a name="standard-dialog-data-validation-routines"></a>标准对话框数据验证例程

本主题列出了用于常见 MFC 对话框控件的标准对话框数据验证 （DDV） 例程。

> [!NOTE]
> 标准对话框数据交换例程在标头文件 afxdd_.h 中定义。 但是，应用程序应包括 afxwin.h。

### <a name="ddv-functions"></a>DDV 功能

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|验证给定控件值中的字符数不超过给定最大值。|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|验证给定的控制值不超过给定**的 BYTE**范围。|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|验证给定控制值不超过给定时间范围。|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|验证给定控制值不超过给定**的双**范围。|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|验证给定控件值不超过给定**的 DWORD**范围。|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|验证给定控制值不超过给定**浮点**范围。|
|[DDV_MinMaxInt](#ddv_minmaxint)|验证给定控件值不超过给定**的 int**范围。|
|[DDV_MinMaxLong](#ddv_minmaxlong)|验证给定的控制值不超过给定**的长距离**。|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|验证给定的控制值不超过给定**的 LONGLONG**范围。|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|验证给定控件值不超过给定日期范围。|
|[DDV_MinMaxShort](#ddv_minmaxshort)|验证给定控制值不超过给定**的短**距离。|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|验证给定滑块控件值位于给定范围内。|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|验证给定控制值不超过给定**的 UINT**范围。|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|验证给定控件值介于两个指定值之间。|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|验证给定的控制值不超过给定**的 ULONGLONG**范围。|

## <a name="ddv_maxchars"></a><a name="ddv_maxchars"></a>DDV_MaxChars

调用`DDV_MaxChars`以验证与*值*关联的控件中的字符量是否不超过*nChars*。

```cpp
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*value*<br/>
对用于验证数据的对话框、窗体视图或控件视图对象的成员变量的引用。

*n查尔斯*<br/>
允许的最大字符数。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddv_minmaxbyte"></a><a name="ddv_minmaxbyte"></a>DDV_MinMaxByte

调用`DDV_MinMaxByte`以验证与*值*关联的控件中的值是否介于*最小值和 maxVal*之间。 *maxVal*

```cpp
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*value*<br/>
对用于验证数据的对话框、窗体视图或控件视图对象的成员变量的引用。

*明瓦尔*<br/>
允许最小值（字节类型）。

*最大瓦尔*<br/>
允许的最大值（字节类型）。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddv_minmaxdatetime"></a><a name="ddv_minmaxdatetime"></a>DDV_MinMaxDateTime

调用`DDV_MinMaxDateTime`以验证日期和时间选取器控件[（CDateTimeCtrl）](../../mfc/reference/cdatetimectrl-class.md)中与*refInValue*关联的时间和日期值是否位于*refMinRange*和*refMaxRange*之间。

```cpp
void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。 您无需删除此对象。

*参考值*<br/>
对与对话框、窗体视图或控件视图对象的成员变量关联的[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象的引用。 此对象包含要验证的数据。

*refMinRange*<br/>
允许的最小日期/时间值。

*refMaxRange*<br/>
允许的最大日期/时间值。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddv_minmaxdouble"></a><a name="ddv_minmaxdouble"></a>DDV_MinMaxDouble

调用`DDV_MinMaxDouble`以验证与*值*关联的控件中的值是否介于*最小值和 maxVal*之间。 *maxVal*

```cpp
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*value*<br/>
对用于验证数据的对话框、窗体视图或控件视图对象的成员变量的引用。

*明瓦尔*<br/>
允许的最小值（类型**为双**精度值）。

*最大瓦尔*<br/>
允许的最大值（类型**为双**精度值）。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddv_minmaxdword"></a><a name="ddv_minmaxdword"></a>DDV_MinMaxDWord

调用`DDV_MinMaxDWord`以验证与*值*关联的控件中的值是否介于*最小值和 maxVal*之间。 *maxVal*

```cpp
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*value*<br/>
对用于验证数据的对话框、窗体视图或控件视图对象的成员变量的引用。

*明瓦尔*<br/>
允许最小值（DWORD 类型）。

*最大瓦尔*<br/>
允许的最大值（DWORD 类型）。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddv_minmaxfloat"></a><a name="ddv_minmaxfloat"></a>DDV_MinMaxFloat

调用`DDV_MinMaxFloat`以验证与*值*关联的控件中的值是否介于*最小值和 maxVal*之间。 *maxVal*

```cpp
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*value*<br/>
对用于验证数据的对话框、窗体视图或控件视图对象的成员变量的引用。

*明瓦尔*<br/>
允许的最小值（类型**浮点**）。

*最大瓦尔*<br/>
允许的最大值 **（浮动类型**）。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddv_minmaxint"></a><a name="ddv_minmaxint"></a>DDV_MinMaxInt

调用`DDV_MinMaxInt`以验证与*值*关联的控件中的值是否介于*最小值和 maxVal*之间。 *maxVal*

```cpp
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*value*<br/>
对用于验证数据的对话框、窗体视图或控件视图对象的成员变量的引用。

*明瓦尔*<br/>
允许的最小值（**类型 int**）。

*最大瓦尔*<br/>
允许的最大值（**类型 int**）。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddv_minmaxlong"></a><a name="ddv_minmaxlong"></a>DDV_MinMaxLong

调用`DDV_MinMaxLong`以验证与*值*关联的控件中的值是否介于*最小值和 maxVal*之间。 *maxVal*

```cpp
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*value*<br/>
对用于验证数据的对话框、窗体视图或控件视图对象的成员变量的引用。

*明瓦尔*<br/>
允许的最小值（**类型长**）。

*最大瓦尔*<br/>
允许的最大值（**类型长**）。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddv_minmaxlonglong"></a><a name="ddv_minmaxlonglong"></a>DDV_MinMaxLongLong

调用`DDV_MinMaxLongLong`以验证与*值*关联的控件中的值是否介于*最小值和 maxVal*之间。 *maxVal*

```cpp
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*value*<br/>
对用于验证数据的对话框、窗体视图或控件视图对象的成员变量的引用。

*明瓦尔*<br/>
允许最小值（龙龙类型）。

*最大瓦尔*<br/>
允许的最大值（龙龙类型）。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddv_minmaxmonth"></a><a name="ddv_minmaxmonth"></a>DDV_MinMaxMonth

调用`DDV_MinMaxMonth`以验证与*refValue*关联的月份日历控件[（CMonthCalCtrl）](../../mfc/reference/cmonthcalctrl-class.md)中的时间/日期值是否位于*refMinRange*和*refMaxRange*之间。

```cpp
void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*参考值*<br/>
对类型`CTime`的对象或与`COleDateTime`对话框、窗体视图或控件视图对象的成员变量关联的对象的引用。 此对象包含要验证的数据。 MFC 在调用时`DDV_MinMaxMonth`传递此引用。

*refMinRange*<br/>
允许的最小日期/时间值。

*refMaxRange*<br/>
允许的最大日期/时间值。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddv_minmaxshort"></a><a name="ddv_minmaxshort"></a>DDV_MinMaxShort

调用`DDV_MinMaxShort`以验证与*值*关联的控件中的值是否介于*最小值和 maxVal*之间。 *maxVal*

```cpp
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*value*<br/>
对用于验证数据的对话框、窗体视图或控件视图对象的成员变量的引用。

*明瓦尔*<br/>
允许的最小值（**短**型）。

*最大瓦尔*<br/>
允许的最大值（**短**型）。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddv_minmaxslider"></a><a name="ddv_minmaxslider"></a>DDV_MinMaxSlider

调用`DDV_MinMaxSlider`以验证与*值*关联的控件中的值是否介于*最小值和 maxVal*之间。 *maxVal*

```cpp
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*value*<br/>
对要验证的值的引用。 此参数保留或设置滑块控件的当前拇指位置。

*明瓦尔*<br/>
允许的最小值。

*最大瓦尔*<br/>
允许的最大值。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关滑块控件的信息，请参阅[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddv_minmaxuint"></a><a name="ddv_minmaxuint"></a>DDV_MinMaxUInt

调用`DDV_MinMaxUInt`以验证与*值*关联的控件中的值是否介于*最小值和 maxVal*之间。 *maxVal*

```cpp
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*value*<br/>
对用于验证数据的对话框、窗体视图或控件视图对象的成员变量的引用。

*明瓦尔*<br/>
允许最小值（UINT 类型）。

*最大瓦尔*<br/>
允许的最大值（UINT 类型）。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddv_minmaxulonglong"></a><a name="ddv_minmaxulonglong"></a>DDV_MinMaxULongLong

调用`DDV_MinMaxULongLong`以验证与*值*关联的控件中的值是否介于*最小值和 maxVal*之间。 *maxVal*

```cpp
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*value*<br/>
对用于验证数据的对话框、窗体视图或控件视图对象的成员变量的引用。

*明瓦尔*<br/>
允许最小值（ULONGLONG 类型）。

*最大瓦尔*<br/>
允许的最大值（ULONGLONG 类型）。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标题**afxdd_.h

## <a name="ddv_minmaxunsigned"></a>DDV_MinMaxUnsigned

调用`DDV_MinMaxUnsigned`以验证与*值*关联的控件中的值是否介于*最小值和 maxVal*之间。 *maxVal*

### <a name="syntax"></a>语法

```cpp
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*value*<br/>
对用于验证数据的对话框、窗体视图或控件视图对象的成员变量的引用。

*明瓦尔*<br/>
允许的最小值（**未签名**类型）。

*最大瓦尔*<br/>
允许的最大值（**类型未符号**）。

### <a name="remarks"></a>备注

有关 DDV 的详细信息，请参阅[对话数据交换和验证](../dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

**标题：** afxdd_.h

## <a name="see-also"></a>另请参阅

[标准对话数据交换例程](standard-dialog-data-exchange-routines.md)<br/>
[MFC 宏和全局函数](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
