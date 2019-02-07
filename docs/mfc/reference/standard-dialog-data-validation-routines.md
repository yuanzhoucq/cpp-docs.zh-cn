---
title: 标准对话框数据验证例程
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: dce982f76e25da424c02d621c1b760ec29e88918
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850159"
---
# <a name="standard-dialog-data-validation-routines"></a>标准对话框数据验证例程

本主题列出了用于常见的 MFC 对话框控件的标准对话框数据验证 (DDV) 例程。

> [!NOTE]
>  标准对话框数据交换例程标头文件 afxdd_.h 中定义。 但是，应用程序应包括 afxwin.h。

### <a name="ddv-functions"></a>DDV 函数

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|验证给定的控件值中的字符数不超过给定的最大值。|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|验证给定的控件值不超过给定**字节**范围。|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|验证给定的控件值不超过给定的时间范围。|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|验证给定的控件值不超过给定**double**范围。|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|验证给定的控件值不超过给定**DWORD**范围。|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|验证给定的控件值不超过给定**float**范围。|
|[DDV_MinMaxInt](#ddv_minmaxint)|验证给定的控件值不超过给定**int**范围。|
|[DDV_MinMaxLong](#ddv_minmaxlong)|验证给定的控件值不超过给定**长**范围。|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|验证给定的控件值不超过给定**LONGLONG**范围。|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|验证给定的控件值不超出给定的日期范围。|
|[DDV_MinMaxShort](#ddv_minmaxshort)|验证给定的控件值不超过给定**短**范围。|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|验证给定的滑块控件值处于给定范围内。|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|验证给定的控件值不超过给定**UINT**范围。|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|验证给定的控件值介于两个指定值之间。|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|验证给定的控件值不超过给定**ULONGLONG**范围。|

##  <a name="ddv_maxchars"></a>  DDV_MaxChars

调用`DDV_MaxChars`若要验证与相关联的控件中的字符量*值*不超过*nChars*。

```
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*值*<br/>
对对话框、 窗体视图或控件视图对象与其数据进行验证的成员变量的引用。

*nChars*<br/>
允许的字符的最大数目。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_.h

##  <a name="ddv_minmaxbyte"></a>  DDV_MinMaxByte

调用`DDV_MinMaxByte`若要验证控件中的值与相关联*值*之间*minVal*并*maxVal*。

```
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*值*<br/>
对对话框、 窗体视图或控件视图对象与其数据进行验证的成员变量的引用。

*minVal*<br/>
（的类型为 BYTE） 允许的最小值。

*maxVal*<br/>
（的类型为 BYTE） 允许的最大值。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_.h

##  <a name="ddv_minmaxdatetime"></a>  DDV_MinMaxDateTime

调用`DDV_MinMaxDateTime`若要验证的日期和时间选取器中的时间/日期值控制 ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) 与关联*refValue*之间*refMinRange*并*refMaxRange*。

```
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
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。 不需要删除此对象。

*refValue*<br/>
对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)与对话框、 窗体视图或控件视图对象的成员变量关联的对象。 此对象包含要验证的数据。

*refMinRange*<br/>
最小值的日期/时间允许的值。

*refMaxRange*<br/>
允许的最大日期/时间值。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_.h

##  <a name="ddv_minmaxdouble"></a>  DDV_MinMaxDouble

调用`DDV_MinMaxDouble`若要验证控件中的值与相关联*值*之间*minVal*并*maxVal*。

```
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*值*<br/>
对对话框、 窗体视图或控件视图对象与其数据进行验证的成员变量的引用。

*minVal*<br/>
最小值 (类型的**double**) 允许。

*maxVal*<br/>
最大值 (类型的**double**) 允许。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_.h

##  <a name="ddv_minmaxdword"></a>  DDV_MinMaxDWord

调用`DDV_MinMaxDWord`若要验证控件中的值与相关联*值*之间*minVal*并*maxVal*。

```
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*值*<br/>
对对话框、 窗体视图或控件视图对象与其数据进行验证的成员变量的引用。

*minVal*<br/>
（的类型为 DWORD） 允许的最小值。

*maxVal*<br/>
（的类型为 DWORD） 允许的最大值。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_.h

##  <a name="ddv_minmaxfloat"></a>  DDV_MinMaxFloat

调用`DDV_MinMaxFloat`若要验证控件中的值与相关联*值*之间*minVal*并*maxVal*。

```
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*值*<br/>
对对话框、 窗体视图或控件视图对象与其数据进行验证的成员变量的引用。

*minVal*<br/>
最小值 (类型的**float**) 允许。

*maxVal*<br/>
最大值 (类型的**float**) 允许。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_.h

##  <a name="ddv_minmaxint"></a>  DDV_MinMaxInt

调用`DDV_MinMaxInt`若要验证控件中的值与相关联*值*之间*minVal*并*maxVal*。

```
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*值*<br/>
对对话框、 窗体视图或控件视图对象与其数据进行验证的成员变量的引用。

*minVal*<br/>
最小值 (类型的**int**) 允许。

*maxVal*<br/>
最大值 (类型的**int**) 允许。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_.h

##  <a name="ddv_minmaxlong"></a>  DDV_MinMaxLong

调用`DDV_MinMaxLong`若要验证控件中的值与相关联*值*之间*minVal*并*maxVal*。

```
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*值*<br/>
对对话框、 窗体视图或控件视图对象与其数据进行验证的成员变量的引用。

*minVal*<br/>
最小值 (类型的**长**) 允许。

*maxVal*<br/>
最大值 (类型的**长**) 允许。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_.h

##  <a name="ddv_minmaxlonglong"></a>  DDV_MinMaxLongLong

调用`DDV_MinMaxLongLong`若要验证控件中的值与相关联*值*之间*minVal*并*maxVal*。

```
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*值*<br/>
对对话框、 窗体视图或控件视图对象与其数据进行验证的成员变量的引用。

*minVal*<br/>
类型最小值 （LONGLONG） 允许。

*maxVal*<br/>
类型最大值 （LONGLONG） 允许。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_.h

##  <a name="ddv_minmaxmonth"></a>  DDV_MinMaxMonth

调用`DDV_MinMaxMonth`以验证在月历中的时间/日期值控制 ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) 与关联*refValue*之间*refMinRange*和*refMaxRange*。

```
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
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*refValue*<br/>
对类型的对象的引用`CTime`或`COleDateTime`关联的对话框中的成员变量，窗体视图，或控件视图对象。 此对象包含要验证的数据。 MFC 将传递此引用时`DDV_MinMaxMonth`调用。

*refMinRange*<br/>
最小值的日期/时间允许的值。

*refMaxRange*<br/>
允许的最大日期/时间值。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_.h

##  <a name="ddv_minmaxshort"></a>  DDV_MinMaxShort

调用`DDV_MinMaxShort`若要验证控件中的值与相关联*值*之间*minVal*并*maxVal*。

```
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*值*<br/>
对对话框、 窗体视图或控件视图对象与其数据进行验证的成员变量的引用。

*minVal*<br/>
最小值 (类型的**短**) 允许。

*maxVal*<br/>
最大值 (类型的**短**) 允许。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_.h

##  <a name="ddv_minmaxslider"></a>  DDV_MinMaxSlider

调用`DDV_MinMaxSlider`若要验证控件中的值与相关联*值*之间*minVal*并*maxVal*。

```
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*值*<br/>
要验证的值对的引用。 此参数保留或设置滑块控件的滚动块的当前位置。

*minVal*<br/>
允许的最小值。

*maxVal*<br/>
允许的最大值。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 滑块控件有关的信息，请参阅[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_.h

##  <a name="ddv_minmaxuint"></a>  DDV_MinMaxUInt

调用`DDV_MinMaxUInt`若要验证控件中的值与相关联*值*之间*minVal*并*maxVal*。

```
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*值*<br/>
对对话框、 窗体视图或控件视图对象与其数据进行验证的成员变量的引用。

*minVal*<br/>
（的类型为 UINT） 允许的最小值。

*maxVal*<br/>
（的类型为 UINT） 允许的最大值。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_.h

##  <a name="ddv_minmaxulonglong"></a>  DDV_MinMaxULongLong

调用`DDV_MinMaxULongLong`若要验证控件中的值与相关联*值*之间*minVal*并*maxVal*。

```
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*值*<br/>
对对话框、 窗体视图或控件视图对象与其数据进行验证的成员变量的引用。

*minVal*<br/>
（的类型 ULONGLONG） 允许的最小值。

*maxVal*<br/>
（的类型 ULONGLONG） 允许的最大值。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

  **标头**afxdd_.h

## <a name="ddvminmaxunsigned"></a>DDV_MinMaxUnsigned

调用`DDV_MinMaxUnsigned`若要验证控件中的值与相关联*值*之间*minVal*并*maxVal*。

### <a name="syntax"></a>语法

```
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```

### <a name="parameters"></a>参数

*pDX*<br/>
指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。

*值*<br/>
对对话框、 窗体视图或控件视图对象与其数据进行验证的成员变量的引用。

*minVal*<br/>
最小值 (类型的**无符号**) 允许。

*maxVal*<br/>
最大值 (类型的**无符号**) 允许。

### <a name="remarks"></a>备注

DDV 有关详细信息，请参阅[对话框数据交换和验证](../dialog-data-exchange-and-validation.md)。

### <a name="requirements"></a>要求

**标头：** afxdd_.h

## <a name="see-also"></a>请参阅

[标准对话框数据交换例程](standard-dialog-data-exchange-routines.md)<br/>
[宏和全局函数](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)

