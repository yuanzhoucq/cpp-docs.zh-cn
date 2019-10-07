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
ms.openlocfilehash: f5c235008b72996424e01ee912ca78ecffab450a
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741579"
---
# <a name="ccolordialog-class"></a>CColorDialog 类

允许将颜色选择对话框合并到应用程序中。

## <a name="syntax"></a>语法

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CColorDialog::CColorDialog](#ccolordialog)|构造 `CColorDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CColorDialog::DoModal](#domodal)|显示 "颜色" 对话框，允许用户进行选择。|
|[CColorDialog::GetColor](#getcolor)|返回一个`COLORREF`结构，该结构包含选定颜色的值。|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|检索用户创建的自定义颜色。|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|强制当前颜色选择指定的颜色。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|重写以验证在对话框中输入的颜色。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CColorDialog::m_cc](#m_cc)|用于自定义对话框的设置的结构。|

## <a name="remarks"></a>备注

`CColorDialog`对象是一个对话框，其中包含为显示系统定义的颜色的列表。 用户可以从列表中选择或创建特定的颜色，该颜色随后会在对话框退出时报告回应用程序。

若要构造`CColorDialog`对象，请使用提供的构造函数或派生新类并使用您自己的自定义构造函数。

构造该对话框后，您可以设置或修改[m_cc](#m_cc)结构中的任何值以初始化对话框控件的值。 *M_cc*结构的类型为[CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1)。

初始化对话框的控件后，调用`DoModal`成员函数以显示对话框，并允许用户选择颜色。 `DoModal`返回用户对对话框的 "确定" （IDOK）或 "取消" （IDCANCEL）按钮的选择。

如果`DoModal`返回 IDOK，则可以使用`CColorDialog`的成员函数来检索用户输入的信息。

您可以使用 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)函数来确定初始化对话框期间是否发生了错误，并了解有关错误的详细信息。

`CColorDialog`依赖于 COMMDLG。Windows 版本3.1 及更高版本附带的 DLL 文件。

若要自定义对话框，从`CColorDialog`派生类，提供自定义对话框模板，并添加消息映射以处理来自扩展控件的通知消息。 所有未处理的消息都应传递到基类。

不需要自定义挂钩函数。

> [!NOTE]
>  在某些安装中`CColorDialog` ，如果已使用框架使其他`CDialog`对象变为灰色，则对象不会以灰色背景显示。

有关使用`CColorDialog`的详细信息，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>要求

**标头：** afxdlgs

##  <a name="ccolordialog"></a>CColorDialog::CColorDialog

构造 `CColorDialog` 对象。

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*clrInit*<br/>
默认颜色选择。 如果未指定任何值，则默认值为 RGB （0，0，0）（黑色）。

*dwFlags*<br/>
一组用于自定义对话框的函数和外观的标志。 有关详细信息，请参阅 Windows SDK 中的[CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1)结构。

*pParentWnd*<br/>
指向对话框的父窗口或所有者窗口的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

##  <a name="domodal"></a>CColorDialog：:D oModal

调用此函数以显示 Windows common color 对话框，并允许用户选择颜色。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

IDOK 或 IDCANCEL。 如果返回 IDCANCEL，则调用 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)函数来确定是否发生了错误。

IDOK 和 IDCANCEL 是常量，用于指示用户是否选择了 "确定" 或 "取消" 按钮。

### <a name="remarks"></a>备注

如果要通过设置[m_cc](#m_cc)结构的成员来初始化各种颜色对话框选项，应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

调用`DoModal`后，可以调用其他成员函数来检索用户在对话框中输入的设置或信息。

### <a name="example"></a>示例

  请参阅[CColorDialog：： CColorDialog](#ccolordialog)的示例。

##  <a name="getcolor"></a>CColorDialog：： GetColor

调用`DoModal`后调用此函数可检索用户所选颜色的相关信息。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

一个[COLORREF](/windows/win32/gdi/colorref)值，该值包含 "颜色" 对话框中所选颜色的 RGB 信息。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

##  <a name="getsavedcustomcolors"></a>CColorDialog::GetSavedCustomColors

`CColorDialog`对象除了选择颜色外，还允许用户定义多达16个自定义颜色。

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>返回值

指向由16个 RGB 颜色值组成的数组的指针，这些值存储用户创建的自定义颜色。

### <a name="remarks"></a>备注

`GetSavedCustomColors`成员函数提供对这些颜色的访问。 可在[DoModal](#domodal)返回 IDOK 后检索这些颜色。

返回的数组中的16个 RGB 值都初始化为 RGB （255255255）（白色）。 用户选择的自定义颜色仅保存在应用程序内的对话框调用之间。 如果希望在应用程序调用之间保存这些颜色，则必须以其他方式（例如在初始化（）中）保存这些颜色。INI）文件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

##  <a name="m_cc"></a>CColorDialog::m_cc

[CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1)类型的结构，其成员存储对话框的特性和值。

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>备注

构造`CColorDialog`对象之后，可以在调用[DoModal](#domodal)成员函数之前，使用*m_cc*设置对话框的各个方面。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

##  <a name="oncolorok"></a>CColorDialog::OnColorOK

重写以验证在对话框中输入的颜色。

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>返回值

如果不应消除对话框，则为非零值;否则，0表示接受输入的颜色。

### <a name="remarks"></a>备注

仅当您希望为用户在 "颜色" 对话框中选择的颜色提供自定义验证时，重写此函数。

用户可以通过以下两种方法之一来选择颜色：

- 单击调色板上的颜色。 然后，所选颜色的 RGB 值将反映在相应的 RGB 编辑框中。

- 在 RGB 编辑框中输入值

通过`OnColorOK`重写，可以拒绝用户为任何特定于应用程序的原因输入到 "公共颜色" 对话框中的颜色。

通常不需要使用此函数，因为框架提供了默认的颜色验证，如果输入的颜色无效，则显示一个消息框。

可以从 `OnColorOK` 内调用 [SetCurrentColor](#setcurrentcolor)，以强制使用颜色选择。 激发`OnColorOK`后（即用户单击 **"确定"** 以接受颜色更改），可以调用[GetColor](#getcolor)来获取新颜色的 RGB 值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

##  <a name="setcurrentcolor"></a>CColorDialog::SetCurrentColor

在调用`DoModal`后调用此函数可强制当前颜色选择为*clr*中指定的颜色值。

```
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>参数

*clr*<br/>
RGB 颜色值。

### <a name="remarks"></a>备注

此函数从消息处理程序或`OnColorOK`中调用。 此对话框将基于*clr*参数的值自动更新用户的选择。

### <a name="example"></a>示例

  请参阅[CColorDialog：： OnColorOK](#oncolorok)的示例。

## <a name="see-also"></a>请参阅

[MFC 示例 MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
