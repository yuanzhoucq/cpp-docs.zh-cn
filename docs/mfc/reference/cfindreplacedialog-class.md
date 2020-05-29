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
ms.openlocfilehash: 7a12d0520d070d74afd9fa91e828970d14c82700
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373859"
---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog 类

允许您在应用程序中实现标准字符串"查找/替换"对话框。

## <a name="syntax"></a>语法

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CFind 替换对话框：：C查找替换对话框](#cfindreplacedialog)|调用此函数以构造对象`CFindReplaceDialog`。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CFind 替换对话框：：创建](#create)|创建并显示`CFindReplaceDialog`对话框。|
|[CFind 替换对话框：：查找下一个](#findnext)|调用此函数以确定用户是否希望查找查找字符串的下一个匹配项。|
|[CFind 替换对话框：：获取查找字符串](#getfindstring)|调用此函数以检索当前查找字符串。|
|[CFind 替换对话框：：获取指示器](#getnotifier)|调用此函数以检索已`FINDREPLACE`注册的消息处理程序中的结构。|
|[CFind 替换对话框：：获取替换字符串](#getreplacestring)|调用此函数以检索当前替换字符串。|
|[CFind 替换对话框：：正在终结](#isterminating)|调用此函数以确定对话框是否终止。|
|[CFind 替换对话框：：匹配案例](#matchcase)|调用此函数以确定用户是否要完全匹配查找字符串的情况。|
|[CFind 替换对话框：：匹配完整字](#matchwholeword)|调用此函数以确定用户是否只想匹配整个单词。|
|[CFind 替换对话框：：全部替换](#replaceall)|调用此函数以确定用户是否希望替换字符串的所有匹配项。|
|[CFind 替换对话框：：替换电流](#replacecurrent)|调用此函数以确定用户是否希望替换当前单词。|
|[CFind 替换对话框：：搜索向下](#searchdown)|调用此函数以确定用户是否希望搜索朝向下方向进行。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CFind 替换对话框：：m_fr](#m_fr)|用于自定义对象的结构`CFindReplaceDialog`。|

## <a name="remarks"></a>备注

与其他 Windows 常见对话框不同，`CFindReplaceDialog`对象是无模式的，允许用户在屏幕上与其他窗互。 有两种`CFindReplaceDialog`对象：查找对话框和查找/替换对话框。 尽管对话框允许用户输入搜索和搜索/替换字符串，但它们不执行任何搜索或替换函数。 您必须将这些添加到应用程序中。

要构造对象`CFindReplaceDialog`，请使用提供的构造函数（没有参数）。 由于这是一个无模式对话框，请使用**新**运算符而不是堆栈上分配对象。

构造`CFindReplaceDialog`对象后，必须调用["创建](#create)成员"函数以创建并显示对话框。

使用[m_fr](#m_fr)结构在调用`Create`之前初始化对话框。 结构`m_fr`为[FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)类型。 有关此结构的详细信息，请参阅 Windows SDK。

为了通知父窗口查找/替换请求，必须使用 Windows[注册窗口消息](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)功能，并在框架窗口中使用处理此已注册消息的帧窗口中[ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message)消息映射宏。

您可以确定用户是否已决定终止具有成员函数的`IsTerminating`对话框。

`CFindReplaceDialog`依赖于 COMMDLG。随 Windows 版本 3.1 及更高版本一起附带的 DLL 文件。

要自定义对话框，请从`CFindReplaceDialog`派生类，并提供自定义对话框模板，并添加消息映射来处理来自扩展控件的通知消息。 任何未处理的消息都应传递到基类。

不需要自定义挂钩功能。

有关 使用`CFindReplaceDialog`的详细信息，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>要求

**标题：** afxdlgs.h

## <a name="cfindreplacedialogcfindreplacedialog"></a><a name="cfindreplacedialog"></a>CFind 替换对话框：：C查找替换对话框

构造 `CFindReplaceDialog` 对象。

```
CFindReplaceDialog();
```

### <a name="remarks"></a>备注

由于`CFindReplaceDialog`对象是无模式对话框，因此必须使用**新**运算符在堆上构造它。

在销毁期间，框架尝试对对话框的指针执行**删除。** 如果在堆栈上创建了对话框，**则此**指针不存在，并且可能会导致未定义的行为。

有关`CFindReplaceDialog`对象构造的详细信息，请参阅[CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)概述。 使用[CFind 替换对话框：创建](#create)成员函数来显示对话框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

## <a name="cfindreplacedialogcreate"></a><a name="create"></a>CFind 替换对话框：：创建

创建并显示"查找"或"查找/替换"对话框对象，具体取决于 的值`bFindDialogOnly`。

```
virtual BOOL Create(
    BOOL bFindDialogOnly,
    LPCTSTR lpszFindWhat,
    LPCTSTR lpszReplaceWith = NULL,
    DWORD dwFlags = FR_DOWN,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*b 仅查找对话*<br/>
将此参数设置为 TRUE 以显示 **"查找"** 对话框。 将其设置为 FALSE 以显示 **"查找/替换**"对话框。

*lpszFind什么*<br/>
显示对话框时指向默认搜索字符串的指针。 如果为 NULL，则对话框不包含默认搜索字符串。

*lpsz 替换与*<br/>
当对话框出现时指向默认替换字符串的指针。 如果为 NULL，则对话框不包含默认替换字符串。

dwFlags**<br/>
可以使用一个或多个标志自定义对话框的设置，使用位或运算符组合使用。 默认值为FR_DOWN，它指定搜索要朝向下方向进行。 有关这些标志的详细信息，请参阅 Windows SDK 中的[FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)结构。

*pparentwnd*<br/>
指向对话框的父窗口或所有者窗口的指针。 这是将接收指示请求查找/替换操作的特殊消息的窗口。 如果 NULL，则使用应用程序的主窗口。

### <a name="return-value"></a>返回值

如果成功创建了对话框对象，则非零;否则 0。

### <a name="remarks"></a>备注

为了通知父窗口查找/替换请求，必须使用 Windows[注册窗口消息](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)函数，其返回值是应用程序实例唯一的消息编号。 帧窗口应具有消息映射条目，该条目声明处理此已注册消息的`OnFindReplace`回调函数（在以下示例中）。 以下代码片段是如何针对名为`CMyRichEditView`的帧窗口类执行此操作的示例：

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

在函数`OnFindReplace`中，您可以使用[CFindReplaceDialog：：FindReplaceDialog：FindNext](#findnext)和[CFindReplaceDialog：：即终止](#isterminating)方法来解释用户的意图，并为查找/替换操作创建代码。

### <a name="example"></a>示例

  请参阅[CFind 替换对话框的示例：cFind替换对话框](#cfindreplacedialog)。

## <a name="cfindreplacedialogfindnext"></a><a name="findnext"></a>CFind 替换对话框：：查找下一个

从回调函数调用此函数以确定用户是否希望查找搜索字符串的下一个匹配项。

```
BOOL FindNext() const;
```

### <a name="return-value"></a>返回值

如果用户想要查找搜索字符串的下一个匹配项，则非零;否则 0。

## <a name="cfindreplacedialoggetfindstring"></a><a name="getfindstring"></a>CFind 替换对话框：：获取查找字符串

从回调函数调用此函数以检索要查找的默认字符串。

```
CString GetFindString() const;
```

### <a name="return-value"></a>返回值

要查找的默认字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetnotifier"></a><a name="getnotifier"></a>CFind 替换对话框：：获取指示器

调用此函数以检索指向当前"查找替换"对话框的指针。

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>参数

*lParam*<br/>
传递到框架窗口的成员函数的`OnFindReplace` *lparam*值。

### <a name="return-value"></a>返回值

指向当前对话框的指针。

### <a name="remarks"></a>备注

应在回调函数中使用它来访问当前对话框、调用其成员函数和访问`m_fr`结构。

### <a name="example"></a>示例

请参阅[CFindReplaceDialog：：创建](#create)有关如何注册 OnFindReplace 处理程序以接收来自"查找替换"对话框的通知的示例。

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetreplacestring"></a><a name="getreplacestring"></a>CFind 替换对话框：：获取替换字符串

调用此函数以检索当前替换字符串。

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>返回值

要替换找到的字符串的默认字符串。

### <a name="example"></a>示例

  请参阅[CFind 替换对话框的示例：获取查找字符串](#getfindstring)。

## <a name="cfindreplacedialogisterminating"></a><a name="isterminating"></a>CFind 替换对话框：：正在终结

在回调函数中调用此函数以确定用户是否已决定终止该对话框。

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>返回值

如果用户决定终止该对话框，则为非零;否则 0。

### <a name="remarks"></a>备注

如果此函数返回非零，则应调用当前对话框`DestroyWindow`的成员函数，并将任何对话框指针变量设置为 NULL。 或者，您还可以存储上次输入的查找/替换文本，并用它来初始化下一个查找/替换对话框。

### <a name="example"></a>示例

  请参阅[CFind 替换对话框的示例：获取查找字符串](#getfindstring)。

## <a name="cfindreplacedialogm_fr"></a><a name="m_fr"></a>CFind 替换对话框：：m_fr

用于自定义`CFindReplaceDialog`对象。

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>备注

`m_fr`是[FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)类型的结构。 其成员存储对话框对象的特征。 构造`CFindReplaceDialog`对象后，可以使用`m_fr`修改对话框中的各种值。

有关此结构的详细信息，请参阅 Windows `FINDREPLACE` SDK 中的结构。

### <a name="example"></a>示例

  请参阅[CFind 替换对话框的示例：cFind替换对话框](#cfindreplacedialog)。

## <a name="cfindreplacedialogmatchcase"></a><a name="matchcase"></a>CFind 替换对话框：：匹配案例

调用此函数以确定用户是否要完全匹配查找字符串的情况。

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>返回值

如果用户想要查找与搜索字符串的情况完全匹配的搜索字符串的匹配项，则非零;否则 0。

## <a name="cfindreplacedialogmatchwholeword"></a><a name="matchwholeword"></a>CFind 替换对话框：：匹配完整字

调用此函数以确定用户是否只想匹配整个单词。

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>返回值

如果用户只想匹配搜索字符串的整个单词，则非零;否则 0。

## <a name="cfindreplacedialogreplaceall"></a><a name="replaceall"></a>CFind 替换对话框：：全部替换

调用此函数以确定用户是否希望替换字符串的所有匹配项。

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>返回值

如果用户请求替换与替换字符串匹配的所有字符串，则非零;否则 0。

## <a name="cfindreplacedialogreplacecurrent"></a><a name="replacecurrent"></a>CFind 替换对话框：：替换电流

调用此函数以确定用户是否希望替换当前单词。

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>返回值

如果用户请求将当前选定的字符串替换为替换字符串，则为非零;否则 0。

## <a name="cfindreplacedialogsearchdown"></a><a name="searchdown"></a>CFind 替换对话框：：搜索向下

调用此函数以确定用户是否希望搜索朝向下方向进行。

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>返回值

如果用户希望搜索朝向下方向进行，则非零;0 如果用户希望搜索朝向上方向进行。

## <a name="see-also"></a>另请参阅

[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
