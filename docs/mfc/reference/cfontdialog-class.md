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
ms.openlocfilehash: 6ece239496def9fd65a95a622ac3c475fe5becea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373825"
---
# <a name="cfontdialog-class"></a>CFontDialog 类

允许您将字体选择对话框合并到应用程序中。

## <a name="syntax"></a>语法

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C方对话：：C方对话](#cfontdialog)|构造 `CFontDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CFontDialog：:Do模态](#domodal)|显示对话框，并允许用户进行选择。|
|[CFontDialog：获取字符格式](#getcharformat)|检索所选字体的字符格式。|
|[CFontDialog：获取颜色](#getcolor)|返回所选字体的颜色。|
|[CFontDialog：获取当前字体](#getcurrentfont)|将当前所选字体的特征分配给`LOGFONT`结构。|
|[CFontDialog：获取Face名称](#getfacename)|返回所选字体的面名。|
|[CFontDialog：获取大小](#getsize)|返回所选字体的点大小。|
|[CFontDialog：获取样式名称](#getstylename)|返回所选字体的样式名称。|
|[CFontDialog：获得重量](#getweight)|返回所选字体的粗细。|
|[CFontDialog：：是](#isbold)|确定字体是否为粗体。|
|[CFontDialog：：伊塔利奇](#isitalic)|确定字体是否为斜体。|
|[CFontDialog：：是斯特里克](#isstrikeout)|确定字体是否以删除方式显示。|
|[CFontDialog：：正则](#isunderline)|确定字体是否带有下划线。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CFontDialog：m_cf](#m_cf)|用于自定义对象的结构`CFontDialog`。|

## <a name="remarks"></a>备注

对象`CFontDialog`是一个对话框，其中包含系统中当前安装的字体列表。 用户可以从列表中选择特定字体，然后将此选择报告回应用程序。

要构造`CFontDialog`对象，请使用提供的构造函数或派生新的子类，并使用您自己的自定义构造函数。

构造`CFontDialog`对象后，`m_cf`可以使用结构在对话框中初始化控件的值或状态。 [m_cf](#m_cf)结构为[CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw)类型。 有关此结构的详细信息，请参阅 Windows SDK。

初始化对话框对象的控件后，调用`DoModal`成员函数以显示对话框并允许用户选择字体。 `DoModal`返回用户是否选择了"确定 （IDOK）"还是"取消"（IDCANCEL）按钮。

如果`DoModal`返回 IDOK，则可以使用 '的成员`CFontDialog`函数之一来检索用户输入的信息。

您可以使用 Windows [CommDlg 扩展错误](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)功能来确定在对话框的初始化过程中是否发生了错误，并了解有关该错误的详细信息。 有关此功能的详细信息，请参阅 Windows SDK。

`CFontDialog`依赖于 COMMDLG。随 Windows 版本 3.1 及更高版本一起附带的 DLL 文件。

要自定义对话框，请从`CFontDialog`派生类，并提供自定义对话框模板，并添加消息映射来处理来自扩展控件的通知消息。 任何未处理的消息都应传递到基类。

不需要自定义挂钩功能。

有关 使用`CFontDialog`的详细信息，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>要求

**标题：** afxdlgs.h

## <a name="cfontdialogcfontdialog"></a><a name="cfontdialog"></a>C方对话：：C方对话

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

*plf初始*<br/>
指向[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)数据结构的指针，允许您设置字体的某些特征。

*字符格式*<br/>
指向[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)数据结构的指针，允许您在丰富的编辑控件中设置字体的某些特征。

dwFlags**<br/>
指定一个或多个用于选择字体的标记。 可以使用按位“OR”运算符对一个或多个预设值进行组合。 如果修改 `m_cf.Flag` 结构成员，请确保在更改中使用按位“OR”运算符以保持默认行为不变。 有关每个标志的详细信息，请参阅 Windows SDK 中[CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw)结构的说明。

*pdcPrinter*<br/>
一个指向打印机设备上下文的指针。 如果已提供此参数，它将指向要选择其字体的打印机的打印机设备上下文。

*pparentwnd*<br/>
一个指向字体对话框的父窗口或所有者窗口的指针。

### <a name="remarks"></a>备注

请注意，构造函数将自动填充 `CHOOSEFONT` 结构的成员。 仅在要让字体对话框不同于默认字体对话框时，才应该更改这些内容。

> [!NOTE]
> 仅在不支持 Rich Edit 控件时，才存在此函数的第一个版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

## <a name="cfontdialogdomodal"></a><a name="domodal"></a>CFontDialog：:Do模态

调用此功能以显示 Windows 常用字体对话框，并允许用户选择字体。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

IDOK 或 IDCANCEL。 如果返回 IDCANCEL，请调用 Windows [CommDlg 扩展错误](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)功能以确定是否发生了错误。

IDOK 和 IDCANCEL 是指示用户选择"确定"还是"取消"按钮的常量。

### <a name="remarks"></a>备注

如果要通过设置[m_cf](#m_cf)结构的成员来初始化各种字体对话框控件，则应在调用`DoModal`之前执行此操作，但在构造对话框对象之后。

如果`DoModal`返回 IDOK，则可以调用其他成员函数来检索用户输入到对话框中的设置或信息。

### <a name="example"></a>示例

  请参阅[CFontDialog 示例：CFontDialog](#cfontdialog)和[CFontDialog：getColor](#getcolor)。

## <a name="cfontdialoggetcharformat"></a><a name="getcharformat"></a>CFontDialog：获取字符格式

检索所选字体的字符格式。

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>参数

*Cf*<br/>
包含所选字体字符格式信息的[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)结构。

## <a name="cfontdialoggetcolor"></a><a name="getcolor"></a>CFontDialog：获取颜色

调用此功能以检索所选字体颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

选定字体的颜色。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

## <a name="cfontdialoggetcurrentfont"></a><a name="getcurrentfont"></a>CFontDialog：获取当前字体

调用此功能将当前所选字体的特征分配给[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构的成员。

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>参数

*lplf*<br/>
指向结构的`LOGFONT`指针。

### <a name="remarks"></a>备注

提供`CFontDialog`其他成员函数以访问当前字体的单个特征。

如果在调用[DoModal](#domodal)期间调用此函数，它将返回当前选择（用户在对话框中看到或更改的内容）。 如果在调用后调用此函数`DoModal`（仅当返回 IDOK`DoModal`时），它返回用户实际选择的内容。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

## <a name="cfontdialoggetfacename"></a><a name="getfacename"></a>CFontDialog：获取Face名称

调用此功能以检索所选字体的面名。

```
CString GetFaceName() const;
```

### <a name="return-value"></a>返回值

对话框中选择的字体的`CFontDialog`面名。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

## <a name="cfontdialoggetsize"></a><a name="getsize"></a>CFontDialog：获取大小

调用此函数以检索所选字体的大小。

```
int GetSize() const;
```

### <a name="return-value"></a>返回值

字体的大小，以十分之一点表示。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

## <a name="cfontdialoggetstylename"></a><a name="getstylename"></a>CFontDialog：获取样式名称

调用此函数以检索所选字体的样式名称。

```
CString GetStyleName() const;
```

### <a name="return-value"></a>返回值

字体的样式名称。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

## <a name="cfontdialoggetweight"></a><a name="getweight"></a>CFontDialog：获得重量

调用此功能以检索所选字体的权重。

```
int GetWeight() const;
```

### <a name="return-value"></a>返回值

所选字体的粗细。

### <a name="remarks"></a>备注

有关字体权重的详细信息，请参阅[CFont：：：create。](../../mfc/reference/cfont-class.md#createfont)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

## <a name="cfontdialogisbold"></a><a name="isbold"></a>CFontDialog：：是

调用此函数以确定所选字体是否为粗体。

```
BOOL IsBold() const;
```

### <a name="return-value"></a>返回值

如果所选字体启用了粗体特征，则非零;否则 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

## <a name="cfontdialogisitalic"></a><a name="isitalic"></a>CFontDialog：：伊塔利奇

调用此函数以确定所选字体是否为斜体。

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>返回值

如果所选字体启用了斜体特征，则非零;否则 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

## <a name="cfontdialogisstrikeout"></a><a name="isstrikeout"></a>CFontDialog：：是斯特里克

调用此函数以确定所选字体是否显示带删除。

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>返回值

如果所选字体启用了"罢工"特征，则非零;否则 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

## <a name="cfontdialogisunderline"></a><a name="isunderline"></a>CFontDialog：：正则

调用此函数以确定所选字体是否带下划线。

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>返回值

如果所选字体启用了下划线特征，则非零;否则 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

## <a name="cfontdialogm_cf"></a><a name="m_cf"></a>CFontDialog：m_cf

其成员存储对话框对象特征的结构。

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>备注

构造`CFontDialog`对象后，可以使用`m_cf`在调用`DoModal`成员函数之前修改对话框的各个方面。 有关此结构的详细信息，请参阅 Windows SDK 中的[CHOOSEFONT。](/windows/win32/api/commdlg/ns-commdlg-choosefontw)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
