---
title: CMFCColorDialog 类
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
ms.openlocfilehash: 9e018c122cded09e5366c3b349525fa7cc004897
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505338"
---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog 类

`CMFCColorDialog`类表示颜色选择对话框。

## <a name="syntax"></a>语法

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|构造 `CMFCColorDialog` 对象。|
|`CMFCColorDialog::~CMFCColorDialog`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCColorDialog::GetColor](#getcolor)|返回当前选定的颜色。|
|[CMFCColorDialog::GetPalette](#getpalette)|返回颜色的调色板。|
|`CMFCColorDialog::PreTranslateMessage`|转换窗口消息, 然后将其调度到[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函数。 有关语法和详细信息, 请参阅[CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 （重写 `CDialogEx::PreTranslateMessage`。）|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|从系统调色板派生调色板。|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|设置当前选定的颜色。|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|设置最等效于指定 RGB 值的颜色。|
|[CMFCColorDialog::SetPageOne](#setpageone)|选择第一个属性页的 RGB 值。|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|选择第二个属性页的 RGB 值。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|`m_bIsMyPalette`|如果颜色选择对话框使用自己的调色板, 则为 TRUE; 如果对话框使用在`CMFCColorDialog`构造函数中指定的调色板, 则为 FALSE。|
|`m_bPickerMode`|如果用户从选择对话框中选择颜色, 则为 TRUE;否则为 FALSE。|
|`m_btnColorSelect`|用户选定的颜色按钮。|
|`m_CurrentColor`|当前选定的颜色。|
|`m_hcurPicker`|用于选取颜色的光标。|
|`m_NewColor`|预期选择的颜色, 可永久选择或恢复为原始颜色。|
|`m_pColourSheetOne`|指向颜色选择属性表的第一个属性页的指针。|
|`m_pColourSheetTwo`|指向颜色选择属性表的第二个属性页的指针。|
|`m_pPalette`|当前逻辑调色板。|
|`m_pPropSheet`|指向颜色选择对话框的属性表的指针。|
|`m_wndColors`|颜色选取器控件对象。|
|`m_wndStaticPlaceHolder`|作为颜色选取器属性表的占位符的静态控件。|

## <a name="remarks"></a>备注

"颜色选择" 对话框显示为具有两页的属性表。 在第一页上, 从系统调色板中选择一种标准颜色;在第二页上, 选择一种自定义颜色。

可以在堆栈上`CMFCColorDialog`构造对象, 然后调用`DoModal`, 并将初始颜色`CMFCColorDialog`作为参数传递到构造函数。 然后, 颜色选择对话框会创建多个[CMFCColorPickerCtrl 类](../../mfc/reference/cmfccolorpickerctrl-class.md)对象来处理每个调色板。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>示例

下面的示例演示如何使用类中的`CMFCColorDialog`各种方法来配置颜色对话框。 该示例演示如何设置对话框的当前和新的颜色, 以及如何在颜色对话框的两个属性页上设置选定颜色的红色、绿色和蓝色成分。 此示例是[新控件示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>要求

**标头:** afxcolordialog

##  <a name="cmfccolordialog"></a>CMFCColorDialog::CMFCColorDialog

构造 `CMFCColorDialog` 对象。

```
CMFCColorDialog(
    COLORREF clrInit=0,
    DWORD dwFlags=0,
    CWnd* pParentWnd=NULL,
    HPALETTE hPal=NULL);
```

### <a name="parameters"></a>参数

*clrInit*<br/>
中默认颜色选择。 如果未指定任何值, 则默认值为 RGB (0, 0, 0) (黑色)。

*dwFlags*<br/>
[in] 保留。

*pParentWnd*<br/>
中指向对话框的父窗口或所有者窗口的指针。

*hPal*<br/>
中调色板的句柄。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getcolor"></a>CMFCColorDialog:: GetColor

检索用户从 "颜色" 对话框中选择的颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

一个[COLORREF](/windows/win32/gdi/colorref)值, 该值包含 "颜色" 对话框中所选颜色的 RGB 信息。

### <a name="remarks"></a>备注

调用`DoModal`方法后调用此函数。

##  <a name="getpalette"></a>CMFCColorDialog::GetPalette

检索 "当前颜色" 对话框中可用的调色板。

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>返回值

`CPalette` 指向`CMFCColorDialog`在构造函数中指定的对象的指针。

### <a name="remarks"></a>备注

调色板指定用户可以选择的颜色。

##  <a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette

从系统调色板派生调色板。

```
void RebuildPalette();
```

##  <a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor

设置对话框的当前颜色。

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>参数

*rgb*<br/>
中RGB 颜色值

### <a name="remarks"></a>备注

##  <a name="setnewcolor"></a>CMFCColorDialog::SetNewColor

将当前颜色设置为当前调色板中最相似的颜色。

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>参数

*rgb*<br/>
中指定 RGB 颜色的[COLORREF](/windows/win32/gdi/colorref) 。

### <a name="remarks"></a>备注

##  <a name="setpageone"></a>CMFCColorDialog::SetPageOne

在颜色对话框的第一个属性页上显式指定选定颜色的红色、绿色和蓝色分量。

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>参数

*R*<br/>
中指定 RGB 值的红色部分。

*G*<br/>
中指定 RGB 值的绿色部分。

*B*<br/>
中指定 RGB 值的蓝色分量。

### <a name="remarks"></a>备注

##  <a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo

在颜色对话框的第二个属性页上显式指定选定颜色的红色、绿色和蓝色分量。

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>参数

*R*<br/>
中指定 RGB 值的红色部分

*G*<br/>
中指定 RGB 值的绿色部分

*B*<br/>
中指定 RGB 值的蓝色分量

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorPickerCtrl 类](../../mfc/reference/cmfccolorpickerctrl-class.md)
