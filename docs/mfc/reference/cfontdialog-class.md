---
title: CFontDialog 类
ms.date: 11/04/2016
f1_keywords:
- CFontDialog
- AFXDLGS/CFontDialog
- AFXDLGS/CFontDialog::CFontDialog
- AFXDLGS/CFontDialog::DoModal
- AFXDLGS/CFontDialog::GetCharFormat
- AFXDLGS/CFontDialog::GetColor
- AFXDLGS/CFontDialog::GetCurrentFont
- AFXDLGS/CFontDialog::GetFaceName
- AFXDLGS/CFontDialog::GetSize
- AFXDLGS/CFontDialog::GetStyleName
- AFXDLGS/CFontDialog::GetWeight
- AFXDLGS/CFontDialog::IsBold
- AFXDLGS/CFontDialog::IsItalic
- AFXDLGS/CFontDialog::IsStrikeOut
- AFXDLGS/CFontDialog::IsUnderline
- AFXDLGS/CFontDialog::m_cf
helpviewer_keywords:
- CFontDialog [MFC], CFontDialog
- CFontDialog [MFC], DoModal
- CFontDialog [MFC], GetCharFormat
- CFontDialog [MFC], GetColor
- CFontDialog [MFC], GetCurrentFont
- CFontDialog [MFC], GetFaceName
- CFontDialog [MFC], GetSize
- CFontDialog [MFC], GetStyleName
- CFontDialog [MFC], GetWeight
- CFontDialog [MFC], IsBold
- CFontDialog [MFC], IsItalic
- CFontDialog [MFC], IsStrikeOut
- CFontDialog [MFC], IsUnderline
- CFontDialog [MFC], m_cf
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
ms.openlocfilehash: c0d0c37d055d9b337f7b709b4ee3d299daae7658
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741559"
---
# <a name="cfontdialog-class"></a>CFontDialog 类

允许将字体选择对话框合并到应用程序中。

## <a name="syntax"></a>语法

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|构造 `CFontDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CFontDialog::DoModal](#domodal)|显示对话框并允许用户进行选择。|
|[CFontDialog::GetCharFormat](#getcharformat)|检索选定字体的字符格式。|
|[CFontDialog::GetColor](#getcolor)|返回选定字体的颜色。|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|将当前所选字体的特征赋给`LOGFONT`结构。|
|[CFontDialog::GetFaceName](#getfacename)|返回所选字体的字体名称。|
|[CFontDialog::GetSize](#getsize)|返回所选字体的点大小。|
|[CFontDialog::GetStyleName](#getstylename)|返回选定字体的样式名称。|
|[CFontDialog::GetWeight](#getweight)|返回所选字体的粗细。|
|[CFontDialog::IsBold](#isbold)|确定字体是否为粗体。|
|[CFontDialog::IsItalic](#isitalic)|确定字体是否为斜体。|
|[CFontDialog::IsStrikeOut](#isstrikeout)|确定字体是否显示为带删除线。|
|[CFontDialog::IsUnderline](#isunderline)|确定字体是否带下划线。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|用于自定义`CFontDialog`对象的结构。|

## <a name="remarks"></a>备注

`CFontDialog`对象是一个对话框，其中包含当前安装在系统中的字体的列表。 用户可以从列表中选择特定字体，然后将此选择报告回应用程序。

若要构造`CFontDialog`对象，请使用提供的构造函数或派生新的子类，并使用您自己的自定义构造函数。

构造对象后，可以`m_cf`使用结构初始化对话框中控件的值或状态。 `CFontDialog` [M_cf](#m_cf)结构的类型为[CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw)。 有关此结构的详细信息，请参阅 Windows SDK。

初始化对话框对象的控件后，调用`DoModal`成员函数以显示对话框，并允许用户选择字体。 `DoModal`返回用户是否选择了 "确定" （IDOK）或 "取消" （IDCANCEL）按钮。

如果`DoModal`返回 IDOK，则可以使用`CFontDialog`的成员函数来检索用户输入的信息。

您可以使用 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)函数来确定初始化对话框期间是否发生了错误，并了解有关错误的详细信息。 有关此函数的详细信息，请参阅 Windows SDK。

`CFontDialog`依赖于 COMMDLG。Windows 版本3.1 及更高版本附带的 DLL 文件。

若要自定义对话框，从`CFontDialog`派生类，提供自定义对话框模板，并添加消息映射以处理来自扩展控件的通知消息。 所有未处理的消息都应传递到基类。

不需要自定义挂钩函数。

有关使用`CFontDialog`的详细信息，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>要求

**标头：** afxdlgs

##  <a name="cfontdialog"></a>CFontDialog::CFontDialog

构造 `CFontDialog` 对象。

```
CFontDialog(
    LPLOGFONT lplfInitial = NULL,
    DWORD dwFlags = CF_EFFECTS | CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);

CFontDialog(
    const CHARFORMAT& charformat,
    DWORD dwFlags = CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*plfInitial*<br/>
指向[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)数据结构的指针，该结构允许您设置字体的某些特征。

*charFormat*<br/>
指向[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)数据结构的指针，该结构允许您在 rich edit 控件中设置字体的某些特征。

*dwFlags*<br/>
指定一个或多个用于选择字体的标记。 可以使用按位“OR”运算符对一个或多个预设值进行组合。 如果修改 `m_cf.Flag` 结构成员，请确保在更改中使用按位“OR”运算符以保持默认行为不变。 有关上述每个标志的详细信息，请参阅 Windows SDK 中的[CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw)结构说明。

*pdcPrinter*<br/>
一个指向打印机设备上下文的指针。 如果已提供此参数，它将指向要选择其字体的打印机的打印机设备上下文。

*pParentWnd*<br/>
一个指向字体对话框的父窗口或所有者窗口的指针。

### <a name="remarks"></a>备注

请注意，构造函数将自动填充 `CHOOSEFONT` 结构的成员。 仅在要让字体对话框不同于默认字体对话框时，才应该更改这些内容。

> [!NOTE]
>  仅在不支持 Rich Edit 控件时，才存在此函数的第一个版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

##  <a name="domodal"></a>CFontDialog：:D oModal

调用此函数以显示 "Windows 通用字体" 对话框，并允许用户选择字体。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

IDOK 或 IDCANCEL。 如果返回 IDCANCEL，则调用 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)函数来确定是否发生了错误。

IDOK 和 IDCANCEL 是常量，用于指示用户是否选择了 "确定" 或 "取消" 按钮。

### <a name="remarks"></a>备注

如果要通过设置[m_cf](#m_cf)结构的成员来初始化各种字体对话框控件，应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，则可以调用其他成员函数来检索用户在对话框中输入的设置或信息。

### <a name="example"></a>示例

  请参阅[CFontDialog：： CFontDialog](#cfontdialog)和[CFontDialog：： GetColor](#getcolor)的示例。

##  <a name="getcharformat"></a>CFontDialog::GetCharFormat

检索选定字体的字符格式。

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>参数

*cf*<br/>
一个[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)结构，其中包含有关所选字体的字符格式的信息。

##  <a name="getcolor"></a>CFontDialog：： GetColor

调用此函数可检索选定的字体颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

选定字体的颜色。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

##  <a name="getcurrentfont"></a>CFontDialog::GetCurrentFont

调用此函数可将当前所选字体的特征分配给[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构的成员。

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>参数

*lplf*<br/>
指向`LOGFONT`结构的指针。

### <a name="remarks"></a>备注

提供`CFontDialog`其他成员函数以访问当前字体的各个特性。

如果在调用[DoModal](#domodal)期间调用此函数，则它将返回当前选定的内容（用户在对话框中看到或已更改的内容）。 如果在调用`DoModal`后调用此函数（仅在返回 IDOK `DoModal`时调用），则它将返回用户实际选择的内容。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

##  <a name="getfacename"></a>CFontDialog::GetFaceName

调用此函数可检索所选字体的字体名称。

```
CString GetFaceName() const;
```

### <a name="return-value"></a>返回值

`CFontDialog`对话框中所选字体的字体名称。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

##  <a name="getsize"></a>CFontDialog：： GetSize

调用此函数可检索选定字体的大小。

```
int GetSize() const;
```

### <a name="return-value"></a>返回值

字体的大小（以十分之一为点）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

##  <a name="getstylename"></a>CFontDialog::GetStyleName

调用此函数可检索选定字体的样式名称。

```
CString GetStyleName() const;
```

### <a name="return-value"></a>返回值

字体的样式名称。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

##  <a name="getweight"></a>CFontDialog::GetWeight

调用此函数可检索选定字体的粗细。

```
int GetWeight() const;
```

### <a name="return-value"></a>返回值

选定字体的粗细。

### <a name="remarks"></a>备注

有关字体权重的详细信息，请参阅[CFont：： CreateFont](../../mfc/reference/cfont-class.md#createfont)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

##  <a name="isbold"></a>CFontDialog::IsBold

调用此函数可确定所选字体是否为粗体。

```
BOOL IsBold() const;
```

### <a name="return-value"></a>返回值

如果所选字体启用了粗体特征，则为非零值;否则为0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

##  <a name="isitalic"></a>CFontDialog::IsItalic

调用此函数可确定所选字体是否为斜体。

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>返回值

如果所选字体启用了斜体特征，则为非零值;否则为0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

##  <a name="isstrikeout"></a>CFontDialog::IsStrikeOut

调用此函数可确定是否显示带有删除线的所选字体。

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>返回值

如果所选字体启用了删除线特征，则为非零值;否则为0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

##  <a name="isunderline"></a>CFontDialog::IsUnderline

调用此函数可确定所选字体是否带下划线。

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>返回值

如果所选字体已启用下划线特征，则为非零值;否则为0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

##  <a name="m_cf"></a>  CFontDialog::m_cf

一个结构，其成员存储对话框对象的特性。

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>备注

构造`CFontDialog`对象之后，您可以使用`m_cf`在调用`DoModal`成员函数之前修改对话框的各个方面。 有关此结构的详细信息，请参阅 Windows SDK 中的[CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
