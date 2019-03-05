---
title: CMFCColorPickerCtrl 类
ms.date: 11/19/2018
f1_keywords:
- CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SelectCellHexagon
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminanceBarWidth
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetOriginalColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetPalette
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetType
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::DrawCursor
helpviewer_keywords:
- CMFCColorPickerCtrl [MFC], CMFCColorPickerCtrl
- CMFCColorPickerCtrl [MFC], GetColor
- CMFCColorPickerCtrl [MFC], GetHLS
- CMFCColorPickerCtrl [MFC], GetHue
- CMFCColorPickerCtrl [MFC], GetLuminance
- CMFCColorPickerCtrl [MFC], GetSaturation
- CMFCColorPickerCtrl [MFC], SelectCellHexagon
- CMFCColorPickerCtrl [MFC], SetColor
- CMFCColorPickerCtrl [MFC], SetHLS
- CMFCColorPickerCtrl [MFC], SetHue
- CMFCColorPickerCtrl [MFC], SetLuminance
- CMFCColorPickerCtrl [MFC], SetLuminanceBarWidth
- CMFCColorPickerCtrl [MFC], SetOriginalColor
- CMFCColorPickerCtrl [MFC], SetPalette
- CMFCColorPickerCtrl [MFC], SetSaturation
- CMFCColorPickerCtrl [MFC], SetType
- CMFCColorPickerCtrl [MFC], DrawCursor
ms.assetid: b9bbd03c-beb0-4b55-9765-9985fd05e5dc
ms.openlocfilehash: 048430c78dfed4158f6fb84eacc07972b79d8a51
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276004"
---
# <a name="cmfccolorpickerctrl-class"></a>CMFCColorPickerCtrl 类

`CMFCColorPickerCtrl`类提供用于选择颜色的控件的功能。

## <a name="syntax"></a>语法

```
class CMFCColorPickerCtrl : public CButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](#cmfccolorpickerctrl)|构造 `CMFCColorPickerCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCColorPickerCtrl::GetColor](#getcolor)|检索用户选择的颜色。|
|[CMFCColorPickerCtrl::GetHLS](#gethls)|检索用户选择的颜色的色调、 亮度和饱和度值。|
|[CMFCColorPickerCtrl::GetHue](#gethue)|检索用户选择的颜色的色调组件。|
|[CMFCColorPickerCtrl::GetLuminance](#getluminance)|检索用户选择的颜色的亮度组件。|
|[CMFCColorPickerCtrl::GetSaturation](#getsaturation)|检索用户选择的颜色的饱和度组件。|
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|将当前的颜色设置为指定的 RGB 颜色组件或指定的单元格六边形定义的颜色。|
|[CMFCColorPickerCtrl::SetColor](#setcolor)|将当前的颜色设置为指定的 RGB 颜色值。|
|[CMFCColorPickerCtrl::SetHLS](#sethls)|将当前的颜色设置为指定的 HLS 颜色值。|
|[CMFCColorPickerCtrl::SetHue](#sethue)|更改当前选定的颜色的色调组件。|
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|更改当前选定的颜色的亮度组件。|
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|颜色选取器控件中设置的亮度栏的宽度。|
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|设置所选的初始颜色。|
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|设置当前的颜色调色板。|
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|更改当前选定的颜色的饱和度组件。|
|[CMFCColorPickerCtrl::SetType](#settype)|设置要显示的颜色选取器控件的类型。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|显示指向所选颜色的游标之前由框架调用。|

## <a name="remarks"></a>备注

标准颜色从六边形调色板中选择和自定义颜色从亮度栏中选择其中指定使用红/绿/蓝表示法或色调/satuaration/亮度表示法表示的颜色。

下图描绘了几个`CMFCColorPickerCtrl`对象。

![CMFCColorPickerCtrl 对话框](../../mfc/reference/media/colorpicker.png "CMFCColorPickerCtrl 对话框")

`CMFCColorPickerCtrl`支持两个对的样式。 十六进制和 HEX_GREYSCALE 样式是适用于标准颜色选择。 选取器和亮度样式是适用于自定义颜色选择。

执行以下步骤将合并`CMFCColorPickerCtrl`控件到对话框中：

1. 如果您使用**ClassWizard**，将新的按钮控件插入到对话框模板 (因为`CMFCColorPickerCtrl`类继承自`CButton`类)。

1. 插入与新的按钮控件到对话框类相关联的成员变量。 然后将更改从变量的类型`CButton`到`CMFCColorPickerCtrl`。

1. 插入`WM_INITDIALOG`对话框类的消息处理程序。 在处理程序中，设置类型、 调色板和的初始选定的颜色`CMFCColorPickerCtrl`控件。

## <a name="example"></a>示例

下面的示例演示如何配置`CMFCColorPickerCtrl`通过使用中的各种方法的对象`CMFCColorPickerCtrl`类。 该示例演示如何设置选取器控件的类型以及如何设置其颜色、 色调、 亮度和饱和度。 此示例摘自[新的控件示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)

## <a name="requirements"></a>要求

**标头：** afxcolorpickerctrl.h

##  <a name="cmfccolorpickerctrl"></a>  CMFCColorPickerCtrl::CMFCColorPickerCtrl

构造 `CMFCColorPickerCtrl` 对象。

```
CMFCColorPickerCtrl();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="drawcursor"></a>  CMFCColorPickerCtrl::DrawCursor

显示指向所选颜色的游标之前由框架调用。

```
virtual void DrawCursor(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文指针。

*rect*<br/>
[in]指定围绕所选颜色的矩形区域。

### <a name="remarks"></a>备注

当您需要更改的游标指向所选颜色的形状时，重写此方法。

##  <a name="getcolor"></a>  CMFCColorPickerCtrl::GetColor

检索用户选择的颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

所选颜色的 RGB 值。

### <a name="remarks"></a>备注

##  <a name="gethls"></a>  CMFCColorPickerCtrl::GetHLS

检索用户选择的颜色的色调、 亮度和饱和度值。

```
void GetHLS(
    double* hue,
    double* luminance,
    double* saturation);
```

### <a name="parameters"></a>参数

*hue*<br/>
[out]指向双精度值，接收 hue 信息类型的变量的指针。

*luminance*<br/>
[out]指向双精度值，接收亮度信息类型的变量的指针。

*saturation*<br/>
[out]指向双精度值，接收饱和度的信息类型的变量的指针。

### <a name="remarks"></a>备注

##  <a name="gethue"></a>  CMFCColorPickerCtrl::GetHue

检索用户选择的颜色的色调组件。

```
double GetHue() const;
```

### <a name="return-value"></a>返回值

所选颜色的色调组件。

### <a name="remarks"></a>备注

##  <a name="getluminance"></a>  CMFCColorPickerCtrl::GetLuminance

检索用户选择的颜色的亮度组件。

```
double GetLuminance() const;
```

### <a name="return-value"></a>返回值

所选颜色的亮度组件。

### <a name="remarks"></a>备注

##  <a name="getsaturation"></a>  CMFCColorPickerCtrl::GetSaturation

检索用户选择的颜色的饱和度值。

```
double GetSaturation() const;
```

### <a name="return-value"></a>返回值

所选颜色的饱和度组件。

### <a name="remarks"></a>备注

##  <a name="selectcellhexagon"></a>  CMFCColorPickerCtrl::SelectCellHexagon

将当前的颜色设置为指定的 RGB 颜色组件或指定的单元格六边形定义的颜色。

```
void SelectCellHexagon(
    BYTE R,
    BYTE G,
    BYTE B);

BOOL SelectCellHexagon(
    int x,
    int y);
```

### <a name="parameters"></a>参数

*R*<br/>
[in]红色组件中。

*G*<br/>
[in]绿色组件中。

*B*<br/>
[in]蓝色颜色组件中。

*x*<br/>
[in]指向单元格六边形光标的 x 坐标。

*y*<br/>
[in]指向单元格六边形光标的 y 坐标。

### <a name="return-value"></a>返回值

此方法的第二个重载总是返回 FALSE。

### <a name="remarks"></a>备注

此方法将设置当前颜色的颜色对应于颜色选择控件的第一个重载的指定红色、 绿色和蓝色颜色组件。

此方法的第二个重载按指定的游标位置设置为指向单元格六边形颜色的当前颜色。

##  <a name="setcolor"></a>  CMFCColorPickerCtrl::SetColor

将当前的颜色设置为指定的 RGB 颜色值。

```
void SetColor(COLORREF Color);
```

### <a name="parameters"></a>参数

*Color*<br/>
[in]RGB 颜色值。

### <a name="remarks"></a>备注

##  <a name="sethls"></a>  CMFCColorPickerCtrl::SetHLS

将当前的颜色设置为指定的 HLS 颜色值。

```
void SetHLS(
    double hue,
    double luminance,
    double saturation,
    BOOL bInvalidate=TRUE);
```

### <a name="parameters"></a>参数

*hue*<br/>
[in]色调值。

*luminance*<br/>
[in]亮度值。

*saturation*<br/>
[in]饱和度值。

*bInvalidate*<br/>
[in]若要强制立即更新为新的颜色; 该窗口，则返回 TRUE否则为 FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

##  <a name="sethue"></a>  CMFCColorPickerCtrl::SetHue

更改当前选定的颜色的色调。

```
void SetHue(double Hue);
```

### <a name="parameters"></a>参数

*Hue*<br/>
[in]色调值。

### <a name="remarks"></a>备注

##  <a name="setluminance"></a>  CMFCColorPickerCtrl::SetLuminance

更改当前所选颜色的亮度。

```
void SetLuminance(double Luminance);
```

### <a name="parameters"></a>参数

*亮度*<br/>
[in]亮度值。

### <a name="remarks"></a>备注

##  <a name="setluminancebarwidth"></a>  CMFCColorPickerCtrl::SetLuminanceBarWidth

颜色选取器控件中设置的亮度栏的宽度。

```
void SetLuminanceBarWidth(int w);
```

### <a name="parameters"></a>参数

*w*<br/>
[in]亮度栏的宽度以像素度量。

### <a name="remarks"></a>备注

此方法用于调整亮度栏，它位于**自定义**颜色选取器控件的选项卡。 *W*参数指定新的亮度栏的宽度。 如果它超出了四分之三的工作区宽度，则忽略宽度值。

##  <a name="setoriginalcolor"></a>  CMFCColorPickerCtrl::SetOriginalColor

设置所选的初始颜色。

```
void SetOriginalColor(COLORREF ref);
```

### <a name="parameters"></a>参数

*ref*<br/>
[in]RGB 颜色值。

### <a name="remarks"></a>备注

初始化颜色选取器控件时调用此方法。

##  <a name="setpalette"></a>  CMFCColorPickerCtrl::SetPalette

设置当前的颜色调色板。

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>参数

*pPalette*<br/>
[in]指向调色板颜色。

### <a name="remarks"></a>备注

调色板定义颜色选取器控件中显示的颜色数组。

##  <a name="setsaturation"></a>  CMFCColorPickerCtrl::SetSaturation

更改当前所选颜色的饱和度。

```
void SetSaturation(double Saturation);
```

### <a name="parameters"></a>参数

*饱和度*<br/>
[in]饱和度值。

### <a name="remarks"></a>备注

##  <a name="settype"></a>  CMFCColorPickerCtrl::SetType

设置要显示的颜色选取器控件的类型。

```
void SetType(COLORTYPE colorType);
```

### <a name="parameters"></a>参数

*colorType*<br/>
[in]颜色选取器控件类型。

类型由定义`CMFCColorPickerCtrl::COLORTYPE`枚举。 可能的类型为亮度、 选取器、 HEX 和 HEX_GREYSCALE。 默认类型为选取器。

### <a name="remarks"></a>备注

若要指定颜色选取器控件类型，请创建 Windows 控件之前调用此方法。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)
