---
title: CColorDialog 类
ms.date: 11/04/2016
f1_keywords:
- CColorDialog
- AFXDLGS/CColorDialog
- AFXDLGS/CColorDialog::CColorDialog
- AFXDLGS/CColorDialog::DoModal
- AFXDLGS/CColorDialog::GetColor
- AFXDLGS/CColorDialog::GetSavedCustomColors
- AFXDLGS/CColorDialog::SetCurrentColor
- AFXDLGS/CColorDialog::OnColorOK
- AFXDLGS/CColorDialog::m_cc
helpviewer_keywords:
- CColorDialog [MFC], CColorDialog
- CColorDialog [MFC], DoModal
- CColorDialog [MFC], GetColor
- CColorDialog [MFC], GetSavedCustomColors
- CColorDialog [MFC], SetCurrentColor
- CColorDialog [MFC], OnColorOK
- CColorDialog [MFC], m_cc
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
ms.openlocfilehash: 99b4ff27a7686972bcbc85478998b52ed713ab5b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754258"
---
# <a name="ccolordialog-class"></a>CColorDialog 类

允许您将颜色选择对话框合并到应用程序中。

## <a name="syntax"></a>语法

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CColor对话：CColorDialog](#ccolordialog)|构造 `CColorDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CColorDialog：:Do模态](#domodal)|显示颜色对话框，并允许用户进行选择。|
|[CColor对话：获取颜色](#getcolor)|返回包含`COLORREF`所选颜色值的结构。|
|[CColorDialog：获取保存的自定义颜色](#getsavedcustomcolors)|检索用户创建的自定义颜色。|
|[CColor对话：：设置当前颜色](#setcurrentcolor)|将当前颜色选择强制为指定颜色。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CColorDialog：：在ColorOK上](#oncolorok)|覆盖以验证输入到对话框中的颜色。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CColorDialog：m_cc](#m_cc)|用于自定义对话框设置的结构。|

## <a name="remarks"></a>备注

对象`CColorDialog`是一个对话框，其中包含为显示系统定义的颜色列表。 用户可以从列表中选择或创建特定颜色，然后在对话框退出时向应用程序报告该颜色。

要构造`CColorDialog`对象，请使用提供的构造函数或派生一个新类，并使用您自己的自定义构造函数。

构造对话框后，可以设置或修改[m_cc](#m_cc)结构中的任何值，以初始化对话框控件的值。 *m_cc*结构的类型[是CHOOSECOLOR。](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1)

初始化对话框的控件后，调用`DoModal`成员函数以显示对话框并允许用户选择颜色。 `DoModal`返回用户选择的对话框的"确定"（IDOK）或"取消"（IDCANCEL）按钮。

如果`DoModal`返回 IDOK，则可以使用 '的成员`CColorDialog`函数之一来检索用户输入的信息。

您可以使用 Windows [CommDlg 扩展错误](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)功能来确定在对话框的初始化过程中是否发生了错误，并了解有关该错误的详细信息。

`CColorDialog`依赖于 COMMDLG。随 Windows 版本 3.1 及更高版本一起附带的 DLL 文件。

要自定义对话框，请从`CColorDialog`派生类，并提供自定义对话框模板，并添加消息映射来处理来自扩展控件的通知消息。 任何未处理的消息都应传递到基类。

不需要自定义挂钩功能。

> [!NOTE]
> 在某些安装上，如果使用`CColorDialog`框架使其他`CDialog`对象变为灰色，则对象将不会以灰色背景显示。

有关 使用`CColorDialog`的详细信息，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>要求

**标题：** afxdlgs.h

## <a name="ccolordialogccolordialog"></a><a name="ccolordialog"></a>CColor对话：CColorDialog

构造 `CColorDialog` 对象。

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*克利尼特*<br/>
默认颜色选择。 如果未指定值，则默认值为 RGB（0，0，0）（黑色）。

dwFlags**<br/>
自定义对话框的功能和外观的一组标志。 有关详细信息，请参阅 Windows SDK 中的[CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1)结构。

*pparentwnd*<br/>
指向对话框的父窗口或所有者窗口的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

## <a name="ccolordialogdomodal"></a><a name="domodal"></a>CColorDialog：:Do模态

调用此函数以显示 Windows 通用颜色对话框，并允许用户选择颜色。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

IDOK 或 IDCANCEL。 如果返回 IDCANCEL，请调用 Windows [CommDlg 扩展错误](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)功能以确定是否发生了错误。

IDOK 和 IDCANCEL 是指示用户选择"确定"还是"取消"按钮的常量。

### <a name="remarks"></a>备注

如果要通过设置[m_cc](#m_cc)结构的成员来初始化各种颜色对话框选项，则应在调用`DoModal`之前在构造对话框对象之后执行此操作。

调用`DoModal`后 ，可以调用其他成员函数来检索用户输入到对话框中的设置或信息。

### <a name="example"></a>示例

  请参阅[CColorDialog 的示例：CColorDialog](#ccolordialog)。

## <a name="ccolordialoggetcolor"></a><a name="getcolor"></a>CColor对话：获取颜色

调用`DoModal`后调用此功能以检索有关用户选择的颜色的信息。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

包含颜色对话框中选择颜色的 RGB 信息的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

## <a name="ccolordialoggetsavedcustomcolors"></a><a name="getsavedcustomcolors"></a>CColorDialog：获取保存的自定义颜色

`CColorDialog`对象允许用户除了选择颜色外，还允许定义多达 16 种自定义颜色。

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>返回值

指向 16 个 RGB 颜色值的数组的指针，用于存储用户创建的自定义颜色。

### <a name="remarks"></a>备注

成员`GetSavedCustomColors`函数提供对这些颜色的访问。 这些颜色可以在[DoModal](#domodal)返回 IDOK 后检索。

返回的数组中的 16 个 RGB 值中的每一个都初始化为 RGB（255，255，255）（白色）。 用户选择的自定义颜色仅在应用程序中的对话框调用之间保存。 如果要在应用程序的调用之间保存这些颜色，则必须以其他某种方式（如初始化 （） 保存这些颜色。INI） 文件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

## <a name="ccolordialogm_cc"></a><a name="m_cc"></a>CColorDialog：m_cc

类型[CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1)的结构，其成员存储对话框的特征和值。

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>备注

构造`CColorDialog`对象后，可以使用*m_cc*在调用[DoModal](#domodal)成员函数之前设置对话框的各个方面。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

## <a name="ccolordialogoncolorok"></a><a name="oncolorok"></a>CColorDialog：：在ColorOK上

覆盖以验证输入到对话框中的颜色。

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>返回值

如果不应取消对话框，则非零;否则 0 接受输入的颜色。

### <a name="remarks"></a>备注

仅当要提供用户在颜色对话框中选择的颜色的自定义验证时，才覆盖此函数。

用户可以通过以下两种方法之一选择颜色：

- 单击调色板上的颜色。 然后，所选颜色的 RGB 值将反映在相应的 RGB 编辑框中。

- 在 RGB 编辑框中输入值

重写`OnColorOK`允许您拒绝用户出于任何应用程序特定原因输入到公共颜色对话框中的颜色。

通常，您不需要使用此函数，因为框架提供默认的颜色验证，并在输入无效颜色时显示消息框。

可以从内部`OnColorOK`调用[SetCurrentColor](#setcurrentcolor)以强制选择颜色。 一`OnColorOK`旦已触发（即，用户单击 **"确定"** 以接受颜色更改），您可以调用[GetColor](#getcolor)获取新颜色的 RGB 值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

## <a name="ccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CColor对话：：设置当前颜色

调用`DoModal`后调用此函数以强制当前颜色选择到*clr*中指定的颜色值。

```cpp
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>参数

*Clr*<br/>
RGB 颜色值。

### <a name="remarks"></a>备注

此函数是从消息处理程序或`OnColorOK`调用 的。 该对话框将根据*clr*参数的值自动更新用户的选择。

### <a name="example"></a>示例

  请参阅[CColorDialog 的示例：：在ColorOK](#oncolorok)上。

## <a name="see-also"></a>请参阅

[MFC 样品 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
