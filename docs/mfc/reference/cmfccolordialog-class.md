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
ms.openlocfilehash: 1b9f57e46d5ac74dd52f7ddb7ebd90f8888891e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403732"
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
|[CMFCColorDialog::GetColor](#getcolor)|返回当前所选的颜色。|
|[CMFCColorDialog::GetPalette](#getpalette)|返回该颜色的调色板。|
|`CMFCColorDialog::PreTranslateMessage`|将窗口消息调度到之前[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)并[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函数。 有关语法和详细信息，请参阅[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 （重写 `CDialogEx::PreTranslateMessage`。）|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|从系统调色板派生调色板。|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|设置当前所选的颜色。|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|设置颜色最等效于指定的 RGB 值。|
|[CMFCColorDialog::SetPageOne](#setpageone)|选择第一个属性页的 RGB 值。|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|选择第二个属性页的 RGB 值。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|`m_bIsMyPalette`|如果颜色选择对话框使用其自己的调色板，则为 TRUE 或 FALSE，如果对话框的使用调色板中指定`CMFCColorDialog`构造函数。|
|`m_bPickerMode`|虽然用户正在从选择对话框; 选择一种颜色，则返回 TRUE否则为 FALSE。|
|`m_btnColorSelect`|用户已经选择了此颜色按钮。|
|`m_CurrentColor`|当前选定的颜色。|
|`m_hcurPicker`|用于选择一种颜色的光标。|
|`m_NewColor`|预期的所选颜色，可以是永久选择或恢复到原始的颜色。|
|`m_pColourSheetOne`|指向颜色选择属性表的第一个属性页的指针。|
|`m_pColourSheetTwo`|指向颜色选择属性表的第二个属性页的指针。|
|`m_pPalette`|当前逻辑调色板。|
|`m_pPropSheet`|指向颜色选择对话框的属性表的指针。|
|`m_wndColors`|一个颜色选取器控件对象。|
|`m_wndStaticPlaceHolder`|静态控件，其颜色选取器属性表的占位符。|

## <a name="remarks"></a>备注

颜色选择对话框中显示为具有两个页面的属性表。 从系统调色板中; 在第一页上，选择一种标准颜色在第二页上，选择自定义颜色。

您可以构造`CMFCColorDialog`对象在堆栈上，然后调用`DoModal`，将作为参数传递的初始颜色`CMFCColorDialog`构造函数。 然后，颜色选择对话框中创建多个[CMFCColorPickerCtrl 类](../../mfc/reference/cmfccolorpickerctrl-class.md)对象以处理每个颜色调色板。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>示例

下面的示例演示如何使用各种方法中的配置颜色对话框`CMFCColorDialog`类。 该示例演示如何设置当前和新颜色的对话框中，以及如何在颜色对话框中的两个属性页上设置所选颜色的红色、 绿色和蓝色组件。 此示例摘自[新的控件示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>要求

**标头：** afxcolordialog.h

##  <a name="cmfccolordialog"></a>  CMFCColorDialog::CMFCColorDialog

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
[in]默认颜色选择。 如果未不指定任何值，默认值为 RGB(0,0,0) （黑色）。

*dwFlags*<br/>
[in] 保留。

*pParentWnd*<br/>
[in]指向对话框的父级或所有者窗口的指针。

*hPal*<br/>
[in]调色板的句柄颜色。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getcolor"></a>  CMFCColorDialog::GetColor

检索用户从颜色对话框中选择的颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

一个[COLORREF](/windows/desktop/gdi/colorref)值，该值包含在颜色对话框中选择的颜色的 RGB 信息。

### <a name="remarks"></a>备注

调用后调用此函数`DoModal`方法。

##  <a name="getpalette"></a>  CMFCColorDialog::GetPalette

检索当前颜色对话框中可用的调色板。

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>返回值

一个指向`CPalette`中指定的对象`CMFCColorDialog`构造函数。

### <a name="remarks"></a>备注

调色板指定用户可以选择的颜色。

##  <a name="rebuildpalette"></a>  CMFCColorDialog::RebuildPalette

从系统调色板派生调色板。

```
void RebuildPalette();
```

##  <a name="setcurrentcolor"></a>  CMFCColorDialog::SetCurrentColor

设置对话框中的当前颜色。

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>参数

*rgb*<br/>
[in]RGB 颜色值

### <a name="remarks"></a>备注

##  <a name="setnewcolor"></a>  CMFCColorDialog::SetNewColor

将当前的颜色设置为当前最相似的调色板中的颜色。

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>参数

*rgb*<br/>
[in]一个[COLORREF](/windows/desktop/gdi/colorref) ，它指定的 RGB 颜色。

### <a name="remarks"></a>备注

##  <a name="setpageone"></a>  CMFCColorDialog::SetPageOne

颜色对话框的第一个属性页上，显式指定所选颜色的红色、 绿色和蓝色组件。

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>参数

*R*<br/>
[in]指定的 RGB 值的红色组件。

*G*<br/>
[in]指定的 RGB 值的绿色组件。

*B*<br/>
[in]指定的 RGB 值的蓝色组件。

### <a name="remarks"></a>备注

##  <a name="setpagetwo"></a>  CMFCColorDialog::SetPageTwo

颜色对话框的第二个属性页上，显式指定所选颜色的红色、 绿色和蓝色组件。

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>参数

*R*<br/>
[in]指定的 RGB 值的红色组件

*G*<br/>
[in]指定一个 RGB 值的绿色组件

*B*<br/>
[in]指定一个 RGB 值的蓝色组件

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorPickerCtrl 类](../../mfc/reference/cmfccolorpickerctrl-class.md)
