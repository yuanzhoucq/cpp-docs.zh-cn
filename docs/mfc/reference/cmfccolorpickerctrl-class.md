---
title: CMFC颜色拾取器课程
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
ms.openlocfilehash: c3c11db448ab31324367b7f314cd6bfe44c2e96d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367689"
---
# <a name="cmfccolorpickerctrl-class"></a>CMFC颜色拾取器课程

类`CMFCColorPickerCtrl`为用于选择颜色的控件提供功能。

## <a name="syntax"></a>语法

```
class CMFCColorPickerCtrl : public CButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC颜色拾取器：：CMFC颜色拾取器](#cmfccolorpickerctrl)|构造 `CMFCColorPickerCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC颜色拾取器：：获取颜色](#getcolor)|检索用户选择的颜色。|
|[CMFC颜色拾取器：：GetHLS](#gethls)|检索用户选择的颜色的色调、亮度和饱和度值。|
|[CMFC颜色拾取器：：GetHue](#gethue)|检索用户选择的颜色的色调组件。|
|[CMFC颜色拾取器：：获取亮度](#getluminance)|检索用户选择的颜色的亮度组件。|
|[CMFC颜色拾取器：：获取饱和度](#getsaturation)|检索用户选择的颜色的饱和度分量。|
|[CMFC颜色拾取器：：选择CellHexagon](#selectcellhexagon)|将当前颜色设置为指定 RGB 颜色分量或指定单元格六边形定义的颜色。|
|[CMFC颜色拾取器：：设置颜色](#setcolor)|将当前颜色设置为指定的 RGB 颜色值。|
|[CMFC颜色拾取器：：SetHLS](#sethls)|将当前颜色设置为指定的 HLS 颜色值。|
|[CMFC颜色拾取器：：SetHue](#sethue)|更改当前所选颜色的色调分量。|
|[CMFC颜色拾取器：：设置亮度](#setluminance)|更改当前所选颜色的亮度分量。|
|[CMFC颜色拾取器：：设置亮度条宽](#setluminancebarwidth)|设置颜色选取器控件中亮度条的宽度。|
|[CMFC颜色选取器Ctrl：设置原始颜色](#setoriginalcolor)|设置初始所选颜色。|
|[CMFC颜色拾取器：：设置调色板](#setpalette)|设置当前调色板。|
|[CMFC颜色拾取器：：设置饱和度](#setsaturation)|更改当前所选颜色的饱和度分量。|
|[CMFC颜色拾取器：：设置类型](#settype)|设置要显示的颜色选取器控件的类型。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFC颜色拾取器：:D生光标](#drawcursor)|显示指向所选颜色的光标之前由框架调用。|

## <a name="remarks"></a>备注

标准颜色是从六边形调色板中选择的，自定义颜色是从亮度条中选择的，其中使用红色/绿色/蓝色表示法或色调/色度/亮度表示法指定颜色。

下图描述了多个`CMFCColorPickerCtrl`对象。

![CMFCColorPickerCtrl 对话框](../../mfc/reference/media/colorpicker.png "CMFCColorPickerCtrl 对话框")

支持`CMFCColorPickerCtrl`两对样式。 HEX 和 HEX_GREYSCALE 样式适用于标准颜色选择。 PICKER 和 LUMINANCE 样式适用于自定义颜色选择。

执行以下步骤将`CMFCColorPickerCtrl`控件合并到对话框中：

1. 如果使用**ClassWizard，** 请在对话框模板中插入新的按钮控件（因为`CMFCColorPickerCtrl`类是从类继承的）。 `CButton`

1. 将与新按钮控件关联的成员变量插入到对话框类中。 然后将变量类型从`CButton`更改为`CMFCColorPickerCtrl`。

1. 插入`WM_INITDIALOG`对话框类的消息处理程序。 在处理程序中，设置`CMFCColorPickerCtrl`控件的类型、调色板和初始选择颜色。

## <a name="example"></a>示例

下面的示例演示如何使用`CMFCColorPickerCtrl``CMFCColorPickerCtrl`类中的各种方法配置对象。 该示例演示如何设置选取器控件的类型，以及如何设置其颜色、色调、亮度和饱和度。 该示例是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)

## <a name="requirements"></a>要求

**标题：** afxpickerctrl.h

## <a name="cmfccolorpickerctrlcmfccolorpickerctrl"></a><a name="cmfccolorpickerctrl"></a>CMFC颜色拾取器：：CMFC颜色拾取器

构造 `CMFCColorPickerCtrl` 对象。

```
CMFCColorPickerCtrl();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfccolorpickerctrldrawcursor"></a><a name="drawcursor"></a>CMFC颜色拾取器：:D生光标

显示指向所选颜色的光标之前由框架调用。

```
virtual void DrawCursor(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*矩形*<br/>
[在]指定所选颜色周围的矩形区域。

### <a name="remarks"></a>备注

当您需要更改指向所选颜色的光标的形状时，将重写此方法。

## <a name="cmfccolorpickerctrlgetcolor"></a><a name="getcolor"></a>CMFC颜色拾取器：：获取颜色

检索用户选择的颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

所选颜色的 RGB 值。

### <a name="remarks"></a>备注

## <a name="cmfccolorpickerctrlgethls"></a><a name="gethls"></a>CMFC颜色拾取器：：GetHLS

检索用户选择的颜色的色调、亮度和饱和度值。

```
void GetHLS(
    double* hue,
    double* luminance,
    double* saturation);
```

### <a name="parameters"></a>参数

*色调*<br/>
[出]指向接收色调信息的双型变量的指针。

*亮度*<br/>
[出]指向接收亮度信息的双型变量的指针。

*饱和*<br/>
[出]指向接收饱和度信息的双型变量的指针。

### <a name="remarks"></a>备注

## <a name="cmfccolorpickerctrlgethue"></a><a name="gethue"></a>CMFC颜色拾取器：：GetHue

检索用户选择的颜色的色调组件。

```
double GetHue() const;
```

### <a name="return-value"></a>返回值

所选颜色的色调分量。

### <a name="remarks"></a>备注

## <a name="cmfccolorpickerctrlgetluminance"></a><a name="getluminance"></a>CMFC颜色拾取器：：获取亮度

检索用户选择的颜色的亮度组件。

```
double GetLuminance() const;
```

### <a name="return-value"></a>返回值

所选颜色的亮度分量。

### <a name="remarks"></a>备注

## <a name="cmfccolorpickerctrlgetsaturation"></a><a name="getsaturation"></a>CMFC颜色拾取器：：获取饱和度

检索用户选择的颜色的饱和度值。

```
double GetSaturation() const;
```

### <a name="return-value"></a>返回值

所选颜色的饱和度分量。

### <a name="remarks"></a>备注

## <a name="cmfccolorpickerctrlselectcellhexagon"></a><a name="selectcellhexagon"></a>CMFC颜色拾取器：：选择CellHexagon

将当前颜色设置为指定 RGB 颜色分量或指定单元格六边形定义的颜色。

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
[在]红色组件。

*G*<br/>
[在]绿色组件。

*B*<br/>
[在]蓝色组件。

** x <br/>
[在]光标的 x 坐标，它指向单元格六边形。

*Y*<br/>
[在]光标的 y 坐标，它指向单元格六边形。

### <a name="return-value"></a>返回值

此方法的第二个重载始终返回 FALSE。

### <a name="remarks"></a>备注

此方法的第一个重载将当前颜色设置为对应于颜色选择控件指定的红色、绿色和蓝色分量的颜色。

此方法的第二个重载将当前颜色设置为由指定的光标位置指向的单元格六边形的颜色。

## <a name="cmfccolorpickerctrlsetcolor"></a><a name="setcolor"></a>CMFC颜色拾取器：：设置颜色

将当前颜色设置为指定的 RGB 颜色值。

```
void SetColor(COLORREF Color);
```

### <a name="parameters"></a>参数

*彩色*<br/>
[在]RGB 颜色值。

### <a name="remarks"></a>备注

## <a name="cmfccolorpickerctrlsethls"></a><a name="sethls"></a>CMFC颜色拾取器：：SetHLS

将当前颜色设置为指定的 HLS 颜色值。

```
void SetHLS(
    double hue,
    double luminance,
    double saturation,
    BOOL bInvalidate=TRUE);
```

### <a name="parameters"></a>参数

*色调*<br/>
[在]色调值。

*亮度*<br/>
[在]亮度值。

*饱和*<br/>
[在]饱和度值。

*b 无效*<br/>
[在]TRUE 强制窗口立即更新到新颜色;否则，FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

## <a name="cmfccolorpickerctrlsethue"></a><a name="sethue"></a>CMFC颜色拾取器：：SetHue

更改当前所选颜色的色调。

```
void SetHue(double Hue);
```

### <a name="parameters"></a>参数

*Hue*<br/>
[在]色调值。

### <a name="remarks"></a>备注

## <a name="cmfccolorpickerctrlsetluminance"></a><a name="setluminance"></a>CMFC颜色拾取器：：设置亮度

更改当前所选颜色的亮度。

```
void SetLuminance(double Luminance);
```

### <a name="parameters"></a>参数

*亮度*<br/>
[在]亮度值。

### <a name="remarks"></a>备注

## <a name="cmfccolorpickerctrlsetluminancebarwidth"></a><a name="setluminancebarwidth"></a>CMFC颜色拾取器：：设置亮度条宽

设置颜色选取器控件中亮度条的宽度。

```
void SetLuminanceBarWidth(int w);
```

### <a name="parameters"></a>参数

*w*<br/>
[在]以像素为单位的亮度条的宽度。

### <a name="remarks"></a>备注

使用此方法可以调整亮度条的大小，亮度条位于颜色选取器控件的 **"自定义"** 选项卡上。 *w*参数指定亮度条的新宽度。 如果宽度值超过工作区宽度的四分之三，则忽略该值。

## <a name="cmfccolorpickerctrlsetoriginalcolor"></a><a name="setoriginalcolor"></a>CMFC颜色选取器Ctrl：设置原始颜色

设置初始所选颜色。

```
void SetOriginalColor(COLORREF ref);
```

### <a name="parameters"></a>参数

*ref*<br/>
[在]RGB 颜色值。

### <a name="remarks"></a>备注

在颜色选取器控件初始化时调用此方法。

## <a name="cmfccolorpickerctrlsetpalette"></a><a name="setpalette"></a>CMFC颜色拾取器：：设置调色板

设置当前调色板。

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>参数

*pPalette*<br/>
[在]指向调色板的指针。

### <a name="remarks"></a>备注

调色板定义颜色选取器控件中显示的颜色数组。

## <a name="cmfccolorpickerctrlsetsaturation"></a><a name="setsaturation"></a>CMFC颜色拾取器：：设置饱和度

更改当前所选颜色的饱和度。

```
void SetSaturation(double Saturation);
```

### <a name="parameters"></a>参数

*饱和度*<br/>
[在]饱和度值。

### <a name="remarks"></a>备注

## <a name="cmfccolorpickerctrlsettype"></a><a name="settype"></a>CMFC颜色拾取器：：设置类型

设置要显示的颜色选取器控件的类型。

```
void SetType(COLORTYPE colorType);
```

### <a name="parameters"></a>参数

*颜色类型*<br/>
[在]颜色选取器控件类型。

类型由`CMFCColorPickerCtrl::COLORTYPE`枚举定义。 可能的类型包括亮度、拾取器、HEX 和HEX_GREYSCALE。 默认类型为"选取器"。

### <a name="remarks"></a>备注

要指定颜色选取器控件类型，请在创建 Windows 控件之前调用此方法。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColor对话类](../../mfc/reference/cmfccolordialog-class.md)
