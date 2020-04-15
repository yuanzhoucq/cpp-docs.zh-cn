---
title: CMFCColor对话类
ms.date: 11/04/2016
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
helpviewer_keywords:
- CMFCColorDialog [MFC], CMFCColorDialog
- CMFCColorDialog [MFC], GetColor
- CMFCColorDialog [MFC], GetPalette
- CMFCColorDialog [MFC], RebuildPalette
- CMFCColorDialog [MFC], SetCurrentColor
- CMFCColorDialog [MFC], SetNewColor
- CMFCColorDialog [MFC], SetPageOne
- CMFCColorDialog [MFC], SetPageTwo
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
ms.openlocfilehash: 987e4f1e5e89c3c56b58adaad76cfd23d5e26c52
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367717"
---
# <a name="cmfccolordialog-class"></a>CMFCColor对话类

类`CMFCColorDialog`表示颜色选择对话框。

## <a name="syntax"></a>语法

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC颜色对话：：CMFC颜色对话](#cmfccolordialog)|构造 `CMFCColorDialog` 对象。|
|`CMFCColorDialog::~CMFCColorDialog`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC颜色对话：获取颜色](#getcolor)|返回当前所选颜色。|
|[CMFCColor对话：获取调色板](#getpalette)|返回调色板。|
|`CMFCColorDialog::PreTranslateMessage`|在窗口消息发送到[翻译消息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[调度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)窗口功能之前进行翻译。 有关语法和更多信息，请参阅[CWnd：:P重新翻译消息](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 （重写 `CDialogEx::PreTranslateMessage`。）|
|[CMFCColor对话：：重建调色板](#rebuildpalette)|从系统调色板派生调色板。|
|[CMFC颜色对话：：设置当前颜色](#setcurrentcolor)|设置当前所选颜色。|
|[CMFCColor对话：：设置新颜色](#setnewcolor)|设置最等效于指定 RGB 值的颜色。|
|[CMFCColor对话：：SetpageOne](#setpageone)|为第一个属性页选择 RGB 值。|
|[CMFCColor对话：：设置页面二](#setpagetwo)|为第二个属性页选择 RGB 值。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|`m_bIsMyPalette`|如果颜色选择对话框使用其自己的调色板，则为 TRUE;如果对话框使用`CMFCColorDialog`构造函数中指定的调色板，则为 FALSE。|
|`m_bPickerMode`|当用户从选择对话框中选择颜色时为 TRUE;在选择对话框中选择颜色时为 TRUE;否则，FALSE。|
|`m_btnColorSelect`|用户选择的颜色按钮。|
|`m_CurrentColor`|当前选择的颜色。|
|`m_hcurPicker`|用于选取颜色的光标。|
|`m_NewColor`|预期选择的颜色，可以永久选择或还原到原始颜色。|
|`m_pColourSheetOne`|指向颜色选择属性表的第一个属性页的指针。|
|`m_pColourSheetTwo`|指向颜色选择属性表的第二个属性页的指针。|
|`m_pPalette`|当前逻辑调色板。|
|`m_pPropSheet`|指向颜色选择对话框的属性表的指针。|
|`m_wndColors`|颜色选取器控件对象。|
|`m_wndStaticPlaceHolder`|作为颜色选取器属性表的占位符的静态控件。|

## <a name="remarks"></a>备注

颜色选择对话框显示为具有两页的属性表。 在第一页上，您可以从系统调色板中选择标准颜色;然后，从系统调色板中选择标准颜色。在第二页上，您可以选择自定义颜色。

您可以在堆栈上`CMFCColorDialog`构造对象，然后调用`DoModal`，将初始颜色作为参数传递给`CMFCColorDialog`构造函数。 然后，颜色选择对话框创建多个[CMFCColorPickerCtrl 类](../../mfc/reference/cmfccolorpickerctrl-class.md)对象来处理每个调色板。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>示例

下面的示例演示如何使用`CMFCColorDialog`类中的各种方法配置颜色对话框。 该示例演示如何设置对话框的当前颜色和新颜色，以及如何在颜色对话框的两个属性页上设置所选颜色的红色、绿色和蓝色分量。 此示例是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>要求

**标题：** afxcolordialog.h

## <a name="cmfccolordialogcmfccolordialog"></a><a name="cmfccolordialog"></a>CMFC颜色对话：：CMFC颜色对话

构造 `CMFCColorDialog` 对象。

```
CMFCColorDialog(
    COLORREF clrInit=0,
    DWORD dwFlags=0,
    CWnd* pParentWnd=NULL,
    HPALETTE hPal=NULL);
```

### <a name="parameters"></a>参数

*克利尼特*<br/>
[在]默认颜色选择。 如果未指定值，则默认值为 RGB（0，0，0）（黑色）。

dwFlags**<br/>
[in] 保留。

*pparentwnd*<br/>
[在]指向对话框的父窗口或所有者窗口的指针。

*hPal*<br/>
[在]调色板的句柄。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfccolordialoggetcolor"></a><a name="getcolor"></a>CMFC颜色对话：获取颜色

检索用户从颜色对话框中选择的颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

包含颜色对话框中选择颜色的 RGB 信息的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>备注

调用`DoModal`方法后调用此函数。

## <a name="cmfccolordialoggetpalette"></a><a name="getpalette"></a>CMFCColor对话：获取调色板

检索当前颜色对话框中可用的调色板。

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>返回值

指向`CMFCColorDialog`构造函数中`CPalette`指定的对象的指针。

### <a name="remarks"></a>备注

调色板指定用户可以选择的颜色。

## <a name="cmfccolordialogrebuildpalette"></a><a name="rebuildpalette"></a>CMFCColor对话：：重建调色板

从系统调色板派生调色板。

```
void RebuildPalette();
```

## <a name="cmfccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CMFC颜色对话：：设置当前颜色

设置对话框的当前颜色。

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>参数

*Rgb*<br/>
[在]RGB 颜色值

### <a name="remarks"></a>备注

## <a name="cmfccolordialogsetnewcolor"></a><a name="setnewcolor"></a>CMFCColor对话：：设置新颜色

将当前颜色设置为当前调色板中最相似的颜色。

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>参数

*Rgb*<br/>
[在]指定 RGB 颜色的[COLORREF。](/windows/win32/gdi/colorref)

### <a name="remarks"></a>备注

## <a name="cmfccolordialogsetpageone"></a><a name="setpageone"></a>CMFCColor对话：：SetpageOne

在颜色对话框的第一个属性页上显式指定所选颜色的红色、绿色和蓝色分量。

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>参数

*R*<br/>
[在]指定 RGB 值的红色组件。

*G*<br/>
[在]指定 RGB 值的绿色组件。

*B*<br/>
[在]指定 RGB 值的蓝色组件。

### <a name="remarks"></a>备注

## <a name="cmfccolordialogsetpagetwo"></a><a name="setpagetwo"></a>CMFCColor对话：：设置页面二

在颜色对话框的第二个属性页上显式指定所选颜色的红色、绿色和蓝色分量。

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>参数

*R*<br/>
[在]指定 RGB 值的红色组件

*G*<br/>
[在]指定 RGB 值的绿色组件

*B*<br/>
[在]指定 RGB 值的蓝色组件

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC颜色拾取器课程](../../mfc/reference/cmfccolorpickerctrl-class.md)
