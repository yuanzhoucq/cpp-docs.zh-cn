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
ms.openlocfilehash: de48d8f495802bdf1c5f69e7a4edc41153c9599f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264620"
---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog 类

可以在你的应用程序中实现的标准字符串查找/替换对话框。

## <a name="syntax"></a>语法

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|调用此函数来构造`CFindReplaceDialog`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CFindReplaceDialog::Create](#create)|创建并显示`CFindReplaceDialog`对话框。|
|[CFindReplaceDialog::FindNext](#findnext)|调用此函数可确定用户是否想要查找查找字符串的下一个匹配项。|
|[CFindReplaceDialog::GetFindString](#getfindstring)|调用此函数可检索当前查找字符串。|
|[CFindReplaceDialog::GetNotifier](#getnotifier)|调用此函数可检索`FINDREPLACE`中已注册的消息处理程序的结构。|
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|调用此函数可检索当前的替换字符串。|
|[CFindReplaceDialog::IsTerminating](#isterminating)|调用此函数可确定是否终止对话框。|
|[CFindReplaceDialog::MatchCase](#matchcase)|调用此函数可确定用户是否想要完全匹配查找字符串的大小写。|
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|调用此函数可确定用户是否想要与全字匹配。|
|[CFindReplaceDialog::ReplaceAll](#replaceall)|调用此函数可确定用户是否想要替换的字符串的所有匹配项。|
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|调用此函数可确定用户是否想要替换的当前单词。|
|[CFindReplaceDialog::SearchDown](#searchdown)|调用此函数可确定用户是否想继续向下搜索。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CFindReplaceDialog::m_fr](#m_fr)|用于自定义的结构`CFindReplaceDialog`对象。|

## <a name="remarks"></a>备注

与其他 Windows 公共对话框，不同`CFindReplaceDialog`对象是无模式，允许用户屏幕上，则与其他 windows 进行交互。 有两种类型的`CFindReplaceDialog`对象：查找对话框和查找/替换对话框。 尽管该对话框允许用户输入的搜索和搜索/替换字符串，但它们不执行任何搜索或替换函数。 您必须将它们添加到应用程序。

若要构造`CFindReplaceDialog`对象，请使用提供的构造函数 （它具有无参数）。 由于这是一个无模式对话框中，分配上堆使用的对象**新**运算符，而不是在堆栈上。

一次`CFindReplaceDialog`构造对象，必须调用[创建](#create)成员函数来创建和显示该对话框。

使用[m_fr](#m_fr)结构初始化之前，调用对话框`Create`。 `m_fr`结构属于类型[FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea)。 此结构的详细信息，请参阅 Windows SDK。

为了使父窗口的查找/替换请求通知，必须使用 Windows [RegisterWindowMessage](/windows/desktop/api/winuser/nf-winuser-registerwindowmessagea)函数，并使用[ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message)在帧中的消息映射宏处理此已注册的消息的窗口。

您可以确定用户是否已决定终止使用对话框`IsTerminating`成员函数。

`CFindReplaceDialog` 依赖于 COMMDLG。随 Windows 3.1 及更高版本的 DLL 文件。

若要自定义对话框中，派生的类从`CFindReplaceDialog`，提供自定义对话框模板，并添加消息映射来处理从扩展控件的通知消息。 任何未处理的消息应传递给类的基类。

不需要自定义挂钩函数。

有关使用的详细信息`CFindReplaceDialog`，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>要求

**标头：** afxdlgs.h

##  <a name="cfindreplacedialog"></a>  CFindReplaceDialog::CFindReplaceDialog

构造 `CFindReplaceDialog` 对象。

```
CFindReplaceDialog();
```

### <a name="remarks"></a>备注

因为`CFindReplaceDialog`对象是无模式对话框中，必须通过使用构造它在堆上**新**运算符。

在析构过程框架尝试执行**删除此**上指向对话框中的指针。 如果在堆栈上创建的对话框**这**指针不存在，并且可能导致未定义的行为。

有关详细信息的构造`CFindReplaceDialog`对象，请参阅[CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)概述。 使用[CFindReplaceDialog::Create](#create)成员函数以显示该对话框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

##  <a name="create"></a>  CFindReplaceDialog::Create

创建并显示的查找或查找/替换对话框对象，具体取决于值`bFindDialogOnly`。

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
将此参数设置为 TRUE 以显示**查找**对话框。 将其设置为 FALSE，则显示**查找/替换**对话框。

*lpszFindWhat*<br/>
指向对话框出现时的默认搜索字符串的指针。 如果为 NULL，则对话框的不包含默认搜索字符串。

*lpszReplaceWith*<br/>
在对话框出现时的默认值替换字符串的指针。 如果为 NULL，则对话框的不包含默认替换字符串。

*dwFlags*<br/>
可以使用自定义对话框中，使用按位 OR 运算符组合的设置的一个或多个标志。 默认值为 FR_DOWN，指定要向下继续执行搜索。 请参阅[FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea)适用于这些标志的详细信息的 Windows SDK 中的结构。

*pParentWnd*<br/>
指向对话框的父级或所有者窗口的指针。 这是将收到指示请求的查找/替换操作的特殊消息的窗口。 如果为 NULL，则使用该应用程序的主窗口。

### <a name="return-value"></a>返回值

已成功创建对话框对象; 如果非零值否则为 0。

### <a name="remarks"></a>备注

为了使父窗口的查找/替换请求通知，必须使用 Windows [RegisterWindowMessage](/windows/desktop/api/winuser/nf-winuser-registerwindowmessagea)函数的返回值是唯一的应用程序的实例的消息号。 框架窗口应具有一个声明回调函数的消息映射条目 (`OnFindReplace`后面的示例中) 用于处理此已注册的消息。 下面的代码片段示范了如何执行此操作的名为的框架窗口类`CMyRichEditView`:

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

在你`OnFindReplace`函数，通过使用解释用户的意图[CFindReplaceDialog::FindNext](#findnext)和[CFindReplaceDialog::IsTerminating](#isterminating)方法和你创建的代码查找/替换操作。

### <a name="example"></a>示例

  有关示例，请参阅[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)。

##  <a name="findnext"></a>  CFindReplaceDialog::FindNext

调用此函数从回调函数来确定用户是否想要查找搜索字符串的下一个匹配项。

```
BOOL FindNext() const;
```

### <a name="return-value"></a>返回值

如果用户想要查找的搜索字符串中; 下一个匹配项，非零值否则为 0。

##  <a name="getfindstring"></a>  CFindReplaceDialog::GetFindString

调用此函数从回调函数来检索要查找的默认字符串。

```
CString GetFindString() const;
```

### <a name="return-value"></a>返回值

要查找的默认字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getnotifier"></a>  CFindReplaceDialog::GetNotifier

调用此函数可检索指向当前查找替换对话框。

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>参数

*lParam*<br/>
*Lparam*值传递到框架窗口的`OnFindReplace`成员函数。

### <a name="return-value"></a>返回值

指向当前的对话框中的指针。

### <a name="remarks"></a>备注

它应该用于回调函数内访问当前的对话框，请调用其成员函数和访问`m_fr`结构。

### <a name="example"></a>示例

请参阅[CFindReplaceDialog::Create](#create)有关如何注册 OnFindReplace 处理程序以从查找替换对话框中接收通知的示例。

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getreplacestring"></a>  CFindReplaceDialog::GetReplaceString

调用此函数可检索当前的替换字符串。

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>返回值

用来替换找到的字符串默认字符串。

### <a name="example"></a>示例

  有关示例，请参阅[CFindReplaceDialog::GetFindString](#getfindstring)。

##  <a name="isterminating"></a>  CFindReplaceDialog::IsTerminating

调用此回调函数来确定用户是否已决定终止对话框框中的函数。

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>返回值

如果用户已决定终止对话框; 非零值否则为 0。

### <a name="remarks"></a>备注

如果此函数返回非零值，则应调用`DestroyWindow`成员函数的当前对话框框，并将任何对话框指针变量设置为 NULL。 （可选） 你也可以存储上次输入的查找/替换文本和使用它来初始化下一步查找/替换对话框。

### <a name="example"></a>示例

  有关示例，请参阅[CFindReplaceDialog::GetFindString](#getfindstring)。

##  <a name="m_fr"></a>  CFindReplaceDialog::m_fr

用于自定义`CFindReplaceDialog`对象。

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>备注

`m_fr` 是一种类型的结构[FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea)。 其成员存储对话框对象的特征。 构造后`CFindReplaceDialog`对象，可以使用`m_fr`修改在对话框中的各种值。

此结构的详细信息，请参阅`FINDREPLACE`Windows SDK 中的结构。

### <a name="example"></a>示例

  有关示例，请参阅[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)。

##  <a name="matchcase"></a>  CFindReplaceDialog::MatchCase

调用此函数可确定用户是否想要完全匹配查找字符串的大小写。

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>返回值

如果用户想要查找完全匹配; 在搜索字符串的大小写的搜索字符串匹配项，非零值否则为 0。

##  <a name="matchwholeword"></a>  CFindReplaceDialog::MatchWholeWord

调用此函数可确定用户是否想要与全字匹配。

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>返回值

如果用户想要匹配的搜索字符串; 仅完整的字词，非零值否则为 0。

##  <a name="replaceall"></a>  CFindReplaceDialog::ReplaceAll

调用此函数可确定用户是否想要替换的字符串的所有匹配项。

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>返回值

如果用户已请求替换所有匹配的替换字符串的字符串; 非零值否则为 0。

##  <a name="replacecurrent"></a>  CFindReplaceDialog::ReplaceCurrent

调用此函数可确定用户是否想要替换的当前单词。

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>返回值

如果用户已请求的当前所选的字符串替换的替换字符串; 非零值否则为 0。

##  <a name="searchdown"></a>  CFindReplaceDialog::SearchDown

调用此函数可确定用户是否想继续向下搜索。

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>返回值

如果用户想要搜索以向下的方向; 来执行非零值如果用户想要继续向上搜索，则为 0。

## <a name="see-also"></a>请参阅

[CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
