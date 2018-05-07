---
title: CMFCColorPickerCtrl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad7e67cc32621fc30108767493c3a7bffd481b68
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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
|[CMFCColorPickerCtrl::GetHue](#gethue)|检索用户选择的颜色色调组件。|  
|[CMFCColorPickerCtrl::GetLuminance](#getluminance)|检索用户选择的颜色的亮度组件。|  
|[CMFCColorPickerCtrl::GetSaturation](#getsaturation)|检索用户选择的颜色饱和度组件。|  
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|将当前颜色设置为指定的 RGB 颜色组件或指定的单元格六边形定义的颜色。|  
|[CMFCColorPickerCtrl::SetColor](#setcolor)|将当前颜色设置为指定的 RGB 颜色值。|  
|[CMFCColorPickerCtrl::SetHLS](#sethls)|将当前颜色设置为指定的 HLS 颜色值。|  
|[CMFCColorPickerCtrl::SetHue](#sethue)|更改当前所选颜色色调组件。|  
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|更改当前所选颜色的亮度组件。|  
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|设置颜色选取器控件中的亮度条的宽度。|  
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|设置的初始的所选的颜色。|  
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|设置的当前颜色调色板。|  
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|更改当前所选颜色饱和度组件。|  
|[CMFCColorPickerCtrl::SetType](#settype)|设置要显示的颜色选取器控件的类型。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|显示指向所选颜色的游标之前，由框架调用。|  
  
## <a name="remarks"></a>备注  
 六边形调色板中选择标准颜色和自定义颜色选择从亮度栏其中指定使用红色/绿色/蓝色表示法或色调/satuaration/亮度表示法的颜色。  
  
 下图描绘了几个`CMFCColorPickerCtrl`对象。  
  
 ![CMFCColorPickerCtrl 对话框](../../mfc/reference/media/colorpicker.png "颜色选取器")  
  
 `CMFCColorPickerCtrl`支持两个对的样式。 十六进制和 HEX_GREYSCALE 样式适于标准颜色选择。 选取器和亮度样式适于自定义颜色选择。  
  
 执行以下步骤以合并`CMFCColorPickerCtrl`控件插入对话框中：  
  
1.  如果你使用**ClassWizard**，将新的按钮控件插入到你对话框模板 (因为`CMFCColorPickerCtrl`类继承自`CButton`类)。  
  
2.  插入与新的按钮控件到对话框类相关联的成员变量。 然后将更改变量的类型从`CButton`到`CMFCColorPickerCtrl`。  
  
3.  插入`WM_INITDIALOG`对话框类的消息处理程序。 在处理程序中，设置的类型、 调色板和初始所选的颜色`CMFCColorPickerCtrl`控件。  
  
## <a name="example"></a>示例  
 下面的示例演示如何配置`CMFCColorPickerCtrl`通过使用中的各种方法的对象`CMFCColorPickerCtrl`类。 示例演示如何设置的一种选取器控件，以及如何设置其颜色、 色调、 亮度和饱和。 此示例摘自的[新控件示例](../../visual-cpp-samples.md)。  
  
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
 显示指向所选颜色的游标之前，由框架调用。  
  
```  
virtual void DrawCursor(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针。  
  
 [in] `rect`  
 指定围绕所选颜色的矩形区域。  
  
### <a name="remarks"></a>备注  
 当您需要更改形状的指向所选颜色的光标时，重写此方法。  
  
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
 [out] `hue`  
 指向双精度值，接收色调信息的类型的变量的指针。  
  
 [out] `luminance`  
 指向双精度值，接收亮度信息的类型的变量的指针。  
  
 [out] `saturation`  
 指向双精度值，接收饱和度信息的类型的变量的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="gethue"></a>  CMFCColorPickerCtrl::GetHue  
 检索用户选择的颜色色调组件。  
  
```  
double GetHue() const;  
```  
  
### <a name="return-value"></a>返回值  
 所选颜色色调组件。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getluminance"></a>  CMFCColorPickerCtrl::GetLuminance  
 检索用户选择的颜色的亮度组件。  
  
```  
double GetLuminance() const;  
```  
  
### <a name="return-value"></a>返回值  
 所选颜色亮度组件。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getsaturation"></a>  CMFCColorPickerCtrl::GetSaturation  
 检索用户选择的颜色饱和度值。  
  
```  
double GetSaturation() const;  
```  
  
### <a name="return-value"></a>返回值  
 所选颜色饱和度组件。  
  
### <a name="remarks"></a>备注  
  
##  <a name="selectcellhexagon"></a>  CMFCColorPickerCtrl::SelectCellHexagon  
 将当前颜色设置为指定的 RGB 颜色组件或指定的单元格六边形定义的颜色。  
  
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
 [in] `R`  
 红色组件中。  
  
 [in] `G`  
 绿色组件中。  
  
 [in] `B`  
 蓝色组件中。  
  
 [in] `x`  
 游标，用于指向一个单元格六边形 x 坐标。  
  
 [in] `y`  
 游标，用于指向一个单元格六边形 y 坐标。  
  
### <a name="return-value"></a>返回值  
 此方法的第二个重载始终返回`FALSE`。  
  
### <a name="remarks"></a>备注  
 当前颜色对应于颜色选择控件的颜色为此方法设置的第一个重载指定的红色、 绿色和蓝色颜色组件。  
  
 此方法的第二个重载按指定的游标位置将当前颜色设置为指向单元格六边形的颜色。  
  
##  <a name="setcolor"></a>  CMFCColorPickerCtrl::SetColor  
 将当前颜色设置为指定的 RGB 颜色值。  
  
```  
void SetColor(COLORREF Color);
```  
  
### <a name="parameters"></a>参数  
 [in] `Color`  
 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="sethls"></a>  CMFCColorPickerCtrl::SetHLS  
 将当前颜色设置为指定的 HLS 颜色值。  
  
```  
void SetHLS(
    double hue,  
    double luminance,  
    double saturation,  
    BOOL bInvalidate=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `hue`  
 色调值。  
  
 [in] `luminance`  
 一个亮度值。  
  
 [in] `saturation`  
 一个饱和度的值。  
  
 [in] `bInvalidate`  
 `TRUE` 以强制该窗口以立即更新为新的颜色;否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="sethue"></a>  CMFCColorPickerCtrl::SetHue  
 更改当前所选颜色色调。  
  
```  
void SetHue(double Hue);
```  
  
### <a name="parameters"></a>参数  
 [in] `Hue`  
 色调值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setluminance"></a>  CMFCColorPickerCtrl::SetLuminance  
 更改当前所选颜色的亮度。  
  
```  
void SetLuminance(double Luminance);
```  
  
### <a name="parameters"></a>参数  
 [in] `Luminance`  
 一个亮度值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setluminancebarwidth"></a>  CMFCColorPickerCtrl::SetLuminanceBarWidth  
 设置颜色选取器控件中的亮度条的宽度。  
  
```  
void SetLuminanceBarWidth(int w);
```  
  
### <a name="parameters"></a>参数  
 [in] `w`  
 以像素度量亮度条的宽度。  
  
### <a name="remarks"></a>备注  
 使用此方法要调整大小的亮度栏，这将在上**自定义**颜色选取器控件的选项卡。 `w`参数指定新的亮度栏的宽度。 如果它超过四分之三的客户端区域宽度，则忽略宽度值。  
  
##  <a name="setoriginalcolor"></a>  CMFCColorPickerCtrl::SetOriginalColor  
 设置的初始的所选的颜色。  
  
```  
void SetOriginalColor(COLORREF ref);
```  
  
### <a name="parameters"></a>参数  
 [in] `ref`  
 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
 在初始化颜色选取器控件时，请调用此方法。  
  
##  <a name="setpalette"></a>  CMFCColorPickerCtrl::SetPalette  
 设置的当前颜色调色板。  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>参数  
 [in] `pPalette`  
 指向一个调色板。  
  
### <a name="remarks"></a>备注  
 调色板定义颜色选取器控件中显示的颜色数组。  
  
##  <a name="setsaturation"></a>  CMFCColorPickerCtrl::SetSaturation  
 更改当前所选颜色饱和度。  
  
```  
void SetSaturation(double Saturation);
```  
  
### <a name="parameters"></a>参数  
 [in] `Saturation`  
 一个饱和度的值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="settype"></a>  CMFCColorPickerCtrl::SetType  
 设置要显示的颜色选取器控件的类型。  
  
```  
void SetType(COLORTYPE colorType);
```  
  
### <a name="parameters"></a>参数  
 [in] `colorType`  
 颜色选取器控件类型。  
  
 通过定义的类型`CMFCColorPickerCtrl::COLORTYPE`枚举。 可能的类型有`LUMINANCE`， `PICKER`，`HEX`和`HEX_GREYSCALE`。 默认类型为 `PICKER`。  
  
### <a name="remarks"></a>备注  
 若要指定颜色选取器控件类型，请在创建 Windows 控件之前调用此方法。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)
