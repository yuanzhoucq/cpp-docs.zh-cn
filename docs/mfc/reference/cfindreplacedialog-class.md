---
title: CFindReplaceDialog 类
ms.date: 11/04/2016
f1_keywords:
- CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::Create
- AFXDLGS/CFindReplaceDialog::FindNext
- AFXDLGS/CFindReplaceDialog::GetFindString
- AFXDLGS/CFindReplaceDialog::GetNotifier
- AFXDLGS/CFindReplaceDialog::GetReplaceString
- AFXDLGS/CFindReplaceDialog::IsTerminating
- AFXDLGS/CFindReplaceDialog::MatchCase
- AFXDLGS/CFindReplaceDialog::MatchWholeWord
- AFXDLGS/CFindReplaceDialog::ReplaceAll
- AFXDLGS/CFindReplaceDialog::ReplaceCurrent
- AFXDLGS/CFindReplaceDialog::SearchDown
- AFXDLGS/CFindReplaceDialog::m_fr
helpviewer_keywords:
- CFindReplaceDialog [MFC], CFindReplaceDialog
- CFindReplaceDialog [MFC], Create
- CFindReplaceDialog [MFC], FindNext
- CFindReplaceDialog [MFC], GetFindString
- CFindReplaceDialog [MFC], GetNotifier
- CFindReplaceDialog [MFC], GetReplaceString
- CFindReplaceDialog [MFC], IsTerminating
- CFindReplaceDialog [MFC], MatchCase
- CFindReplaceDialog [MFC], MatchWholeWord
- CFindReplaceDialog [MFC], ReplaceAll
- CFindReplaceDialog [MFC], ReplaceCurrent
- CFindReplaceDialog [MFC], SearchDown
- CFindReplaceDialog [MFC], m_fr
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
ms.openlocfilehash: 92429bc17301d6615c87de958f38a717528e9544
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212431"
---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog 类

允许你在应用程序中实现标准字符串 "查找/替换" 对话框。

## <a name="syntax"></a>语法

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CFindReplaceDialog：： CFindReplaceDialog](#cfindreplacedialog)|调用此函数可构造 `CFindReplaceDialog` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CFindReplaceDialog：： Create](#create)|创建并显示一个 `CFindReplaceDialog` 对话框。|
|[CFindReplaceDialog：： FindNext](#findnext)|调用此函数可确定用户是否要查找查找字符串的下一个匹配项。|
|[CFindReplaceDialog：： GetFindString](#getfindstring)|调用此函数可检索当前查找字符串。|
|[CFindReplaceDialog：： GetNotifier](#getnotifier)|调用此函数可检索 `FINDREPLACE` 已注册消息处理程序中的结构。|
|[CFindReplaceDialog：： GetReplaceString](#getreplacestring)|调用此函数可检索当前替换字符串。|
|[CFindReplaceDialog：： IsTerminating](#isterminating)|调用此函数可确定对话框是否正在终止。|
|[CFindReplaceDialog：： MatchCase](#matchcase)|调用此函数可确定用户是否需要完全匹配查找字符串的大小写。|
|[CFindReplaceDialog：： MatchWholeWord](#matchwholeword)|调用此函数可确定用户是否只需要匹配整个单词。|
|[CFindReplaceDialog：： ReplaceAll](#replaceall)|调用此函数可确定用户是否需要替换字符串的所有匹配项。|
|[CFindReplaceDialog：： ReplaceCurrent](#replacecurrent)|调用此函数可确定用户是否需要替换当前单词。|
|[CFindReplaceDialog：： SearchDown](#searchdown)|调用此函数可确定用户是否希望在向下进行搜索。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CFindReplaceDialog：： m_fr](#m_fr)|用于自定义对象的结构 `CFindReplaceDialog` 。|

## <a name="remarks"></a>备注

不同于其他 Windows 公共对话框， `CFindReplaceDialog` 对象是无模式的，允许用户在屏幕上与其他窗口交互。 有两种类型的 `CFindReplaceDialog` 对象： "查找" 对话框和 "查找/替换" 对话框。 虽然对话框允许用户输入搜索和搜索/替换字符串，但它们不执行任何搜索或替换函数。 必须将它们添加到应用程序。

若要构造 `CFindReplaceDialog` 对象，请使用提供的构造函数（没有参数）。 由于这是无模式对话框，因此请使用 **`new`** 运算符（而不是堆栈）在堆上分配对象。

`CFindReplaceDialog`构造对象之后，必须调用[create](#create)成员函数以创建并显示该对话框。

在调用之前，请使用[m_fr](#m_fr)结构来初始化对话框 `Create` 。 `m_fr`结构的类型为[FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)。 有关此结构的详细信息，请参阅 Windows SDK。

为了让父窗口收到 "查找/替换" 请求的通知，您必须使用 Windows [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)函数，并使用您的框架窗口中的[ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message)消息映射宏来处理此注册消息。

您可以确定用户是否已决定通过 `IsTerminating` 成员函数终止对话框。

`CFindReplaceDialog`依赖于 Windows 版本3.1 及更高版本附带的 COMMDLG.DLL 文件。

若要自定义对话框，从派生类 `CFindReplaceDialog` ，提供自定义对话框模板，并添加消息映射以处理来自扩展控件的通知消息。 所有未处理的消息都应传递到基类。

不需要自定义挂钩函数。

有关使用的详细信息 `CFindReplaceDialog` ，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>要求

**标头：** afxdlgs

## <a name="cfindreplacedialogcfindreplacedialog"></a><a name="cfindreplacedialog"></a>CFindReplaceDialog：： CFindReplaceDialog

构造 `CFindReplaceDialog` 对象。

```
CFindReplaceDialog();
```

### <a name="remarks"></a>备注

因为 `CFindReplaceDialog` 对象是无模式对话框，所以必须使用运算符在堆上构造它 **`new`** 。

在析构期间，框架尝试在指向对话框的指针上执行 "**删除**"。 如果在堆栈上创建了对话框，则 **`this`** 指针不存在，可能会导致未定义的行为。

有关对象构造的详细信息 `CFindReplaceDialog` ，请参阅[CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)概述。 使用[CFindReplaceDialog：： Create](#create)成员函数来显示对话框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

## <a name="cfindreplacedialogcreate"></a><a name="create"></a>CFindReplaceDialog：： Create

根据的值，创建并显示 "查找" 或 "查找/替换" 对话框对象 `bFindDialogOnly` 。

```
virtual BOOL Create(
    BOOL bFindDialogOnly,
    LPCTSTR lpszFindWhat,
    LPCTSTR lpszReplaceWith = NULL,
    DWORD dwFlags = FR_DOWN,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*bFindDialogOnly*<br/>
将此参数设置为 TRUE 可显示 "**查找**" 对话框。 将其设置为 FALSE 可显示 "**查找/替换**" 对话框。

*lpszFindWhat*<br/>
当对话框出现时指向默认搜索字符串的指针。 如果为 NULL，则对话框不包含默认搜索字符串。

*lpszReplaceWith*<br/>
当对话框出现时，为默认替换字符串的指针。 如果为 NULL，则对话框不包含默认的替换字符串。

dwFlags**<br/>
可用于自定义对话框的设置的一个或多个标志，使用按位 "或" 运算符组合在一起。 默认值为 FR_DOWN，该值指定搜索将按向下进行。 有关这些标志的详细信息，请参阅 Windows SDK 中的[FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)结构。

*pParentWnd*<br/>
指向对话框的父窗口或所有者窗口的指针。 此窗口将接收特定消息，指示已请求查找/替换操作。 如果为 NULL，则使用应用程序的主窗口。

### <a name="return-value"></a>返回值

如果已成功创建对话框对象，则为非零值;否则为0。

### <a name="remarks"></a>备注

为了让父窗口收到查找/替换请求的通知，您必须使用 Windows [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)函数，该函数的返回值为应用程序实例特有的消息号。 框架窗口应具有一个消息映射条目，该条目声明 `OnFindReplace` 处理此已注册消息的回调函数（在下面的示例中）。 下面的代码片段举例说明如何为名为的框架窗口类执行此 `CMyRichEditView` 操作：

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

在 `OnFindReplace` 函数中，通过使用[CFindReplaceDialog：： FindNext](#findnext)和[CFindReplaceDialog：： IsTerminating](#isterminating)方法解释用户的意图，并为查找/替换操作创建代码。

### <a name="example"></a>示例

  请参阅[CFindReplaceDialog：： CFindReplaceDialog](#cfindreplacedialog)的示例。

## <a name="cfindreplacedialogfindnext"></a><a name="findnext"></a>CFindReplaceDialog：： FindNext

从回调函数调用此函数，以确定用户是否要查找搜索字符串的下一个匹配项。

```
BOOL FindNext() const;
```

### <a name="return-value"></a>返回值

如果用户想要查找搜索字符串的下一个匹配项，则为非零值;否则为0。

## <a name="cfindreplacedialoggetfindstring"></a><a name="getfindstring"></a>CFindReplaceDialog：： GetFindString

从回调函数调用此函数以检索要查找的默认字符串。

```
CString GetFindString() const;
```

### <a name="return-value"></a>返回值

要查找的默认字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetnotifier"></a><a name="getnotifier"></a>CFindReplaceDialog：： GetNotifier

调用此函数可检索指向当前 "查找替换" 对话框的指针。

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>参数

*lParam*<br/>
传递到框架窗口成员函数的*lparam*值 `OnFindReplace` 。

### <a name="return-value"></a>返回值

指向当前对话框的指针。

### <a name="remarks"></a>备注

它应在回调函数中用于访问当前对话框、调用其成员函数和访问 `m_fr` 结构。

### <a name="example"></a>示例

有关如何注册 OnFindReplace 处理程序以从 "查找替换" 对话框接收通知的示例，请参阅[CFindReplaceDialog：： Create](#create) 。

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetreplacestring"></a><a name="getreplacestring"></a>CFindReplaceDialog：： GetReplaceString

调用此函数可检索当前替换字符串。

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>返回值

用于替换所找到字符串的默认字符串。

### <a name="example"></a>示例

  请参阅[CFindReplaceDialog：： GetFindString](#getfindstring)的示例。

## <a name="cfindreplacedialogisterminating"></a><a name="isterminating"></a>CFindReplaceDialog：： IsTerminating

在回调函数中调用此函数，以确定用户是否已决定终止对话框。

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>返回值

如果用户已决定终止对话框，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果此函数返回非零值，则应调用 `DestroyWindow` 当前对话框的成员函数，并将任何对话框指针变量设置为 NULL。 （可选）还可以存储上次输入的 "查找/替换" 文本，并使用它来初始化下一个 "查找/替换" 对话框。

### <a name="example"></a>示例

  请参阅[CFindReplaceDialog：： GetFindString](#getfindstring)的示例。

## <a name="cfindreplacedialogm_fr"></a><a name="m_fr"></a>CFindReplaceDialog：： m_fr

用于自定义 `CFindReplaceDialog` 对象。

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>备注

`m_fr`是[FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)类型的结构。 其成员存储对话框对象的特性。 构造对象之后 `CFindReplaceDialog` ，您可以使用 `m_fr` 修改对话框中的各种值。

有关此结构的详细信息，请参阅 `FINDREPLACE` Windows SDK 中的结构。

### <a name="example"></a>示例

  请参阅[CFindReplaceDialog：： CFindReplaceDialog](#cfindreplacedialog)的示例。

## <a name="cfindreplacedialogmatchcase"></a><a name="matchcase"></a>CFindReplaceDialog：： MatchCase

调用此函数可确定用户是否需要完全匹配查找字符串的大小写。

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>返回值

如果用户想要查找与搜索字符串大小写完全匹配的搜索字符串的匹配项，则为非零值;否则为0。

## <a name="cfindreplacedialogmatchwholeword"></a><a name="matchwholeword"></a>CFindReplaceDialog：： MatchWholeWord

调用此函数可确定用户是否只需要匹配整个单词。

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>返回值

如果用户只想匹配搜索字符串的整个单词，则为非零值;否则为0。

## <a name="cfindreplacedialogreplaceall"></a><a name="replaceall"></a>CFindReplaceDialog：： ReplaceAll

调用此函数可确定用户是否需要替换字符串的所有匹配项。

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>返回值

如果用户已请求与替换字符串匹配的所有字符串都被替换，则为非零值;否则为0。

## <a name="cfindreplacedialogreplacecurrent"></a><a name="replacecurrent"></a>CFindReplaceDialog：： ReplaceCurrent

调用此函数可确定用户是否需要替换当前单词。

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>返回值

如果用户已请求将当前选定的字符串替换为替换字符串，则为非零值;否则为0。

## <a name="cfindreplacedialogsearchdown"></a><a name="searchdown"></a>CFindReplaceDialog：： SearchDown

调用此函数可确定用户是否希望在向下进行搜索。

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>返回值

如果用户希望搜索在向下进行，则为非零值;如果用户希望搜索按向上进行，则为0。

## <a name="see-also"></a>另请参阅

[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
