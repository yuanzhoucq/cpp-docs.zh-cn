---
title: CMFCEditBrowseCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFileBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFolderBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::GetMode
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnAfterUpdate
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnBrowse
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnChangeLayout
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnDrawBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnIllegalFileName
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::SetBrowseButtonImage
helpviewer_keywords:
- CMFCEditBrowseCtrl [MFC], EnableBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFileBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFolderBrowseButton
- CMFCEditBrowseCtrl [MFC], GetMode
- CMFCEditBrowseCtrl [MFC], OnAfterUpdate
- CMFCEditBrowseCtrl [MFC], OnBrowse
- CMFCEditBrowseCtrl [MFC], OnChangeLayout
- CMFCEditBrowseCtrl [MFC], OnDrawBrowseButton
- CMFCEditBrowseCtrl [MFC], OnIllegalFileName
- CMFCEditBrowseCtrl [MFC], SetBrowseButtonImage
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
ms.openlocfilehash: d542af4a87b6f0a33c0344d1d3da76980f8c1a91
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752378"
---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl 类

该`CMFCEditBrowseCtrl`类支持编辑浏览控件，这是一个可编辑的文本框，可选包含浏览按钮。 当用户单击浏览按钮时，此控件会执行自定义操作或显示包含文件浏览器或文件夹浏览器的标准对话框。

## <a name="syntax"></a>语法

```
class CMFCEditBrowseCtrl : public CEdit
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|默认构造函数。|
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCEdit 浏览Ctrl：：启用浏览按钮](#enablebrowsebutton)|启用或禁用（隐藏）浏览按钮。|
|[CMFCEdit 浏览Ctrl：：启用文件浏览按钮](#enablefilebrowsebutton)|启用浏览按钮并将编辑浏览控件置于*文件浏览*模式。|
|[CMFCEdit 浏览Ctrl：：启用文件夹浏览按钮](#enablefolderbrowsebutton)|启用浏览按钮并将编辑浏览控件置于*文件夹浏览*模式。|
|[CMFCEdit 浏览Ctrl：获取模式](#getmode)|返回当前浏览模式。|
|[CMFCEdit 浏览Ctrl：在更新后打开](#onafterupdate)|编辑浏览控件使用浏览操作的结果更新后由框架调用。|
|[CMFCEdit 浏览Ctrl：：在浏览](#onbrowse)|用户单击浏览按钮后由框架调用。|
|[CMFCEdit 浏览Ctrl：：在更改布局上](#onchangelayout)|重绘当前编辑浏览控件。|
|[CMFCEdit 浏览Ctrl：：在绘制浏览按钮](#ondrawbrowsebutton)|由框架调用以绘制浏览按钮。|
|[CMFCEdit 浏览Ctrl：在非法文件名上](#onillegalfilename)|在编辑控件中输入非法文件名时由框架调用。|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|在窗口消息发送到[翻译消息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[调度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)窗口功能之前进行翻译。 有关语法和更多信息，请参阅[CWnd：:P重新翻译消息](../../mfc/reference/cwnd-class.md#pretranslatemessage)。|
|[CMFCEdit 浏览Ctrl：：设置浏览按钮图像](#setbrowsebuttonimage)|为浏览按钮设置自定义图像。|

## <a name="remarks"></a>备注

使用编辑浏览控件选择文件或文件夹名称。 或者，使用 控件执行自定义操作，例如显示对话框。 您可以显示或不显示浏览按钮，也可以在按钮上应用自定义标签或图像。

编辑*浏览控件的浏览模式*确定它是否显示浏览按钮，以及单击该按钮时将执行什么操作。 有关详细信息，请参阅[GetMode](#getmode)方法。

该`CMFCEditBrowseCtrl`类支持以下模式。

- **自定义模式**

   当用户单击浏览按钮时，将执行自定义操作。 例如，可以显示特定于应用程序的对话框。

- **文件模式**

   当用户单击浏览按钮时，将显示一个标准文件选择对话框。

- **文件夹模式**

   当用户单击浏览按钮时，将显示一个标准文件夹选择对话框。

## <a name="how-to-specify-an-edit-browse-control"></a>如何：指定编辑浏览控件

执行以下步骤以在应用程序中合并编辑浏览控件：

1. 如果要实现自定义浏览模式，请从`CMFCEditBrowseCtrl`类派生您自己的类，然后重写[CMFCEditBrowseCtrl：：onBrowse](#onbrowse)方法。 在重写方法中，执行自定义浏览操作，并随结果更新编辑浏览控件。

1. 将`CMFCEditBrowseCtrl`对象或派生的编辑浏览控件对象嵌入到父窗口对象中。

1. 如果使用**类向导**创建对话框，请向对话框窗体添加编辑控件 （ `CEdit`。 此外，添加变量以访问标头文件中的控件。 在头文件中，将变量的类型从`CEdit`更改为`CMFCEditBrowseCtrl`。 将自动创建编辑浏览控件。 如果不使用**类向导**，请向标头文件添加变量`CMFCEditBrowseCtrl`，然后调用其`Create`方法。

1. 如果将编辑浏览控件添加到对话框中，请使用**ClassWizard**工具设置数据交换。

1. 调用[启用文件夹浏览按钮](#enablefolderbrowsebutton)，[启用文件浏览按钮](#enablefilebrowsebutton)，或[启用浏览按钮](#enablebrowsebutton)方法，以设置浏览模式并显示浏览按钮。 调用[GetMode](#getmode)方法以获取当前浏览模式。

1. 要为浏览按钮提供自定义图像，请调用[SetBrowseButtonImage](#setbrowsebuttonimage)方法或重写[OnDrawBrowseButton](#ondrawbrowsebutton)方法。

1. 要从编辑浏览控件中删除浏览按钮，请调用[启用BrowseButton](#enablebrowsebutton)方法，将*bEnable*参数设置为 FALSE。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>示例

下面的示例演示如何在`CMFCEditBrowseCtrl`类中使用两种方法：`EnableFolderBrowseButton`和`EnableFileBrowseButton`。 此示例是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>要求

**标题：** afxeditbrowsectrl.h

## <a name="cmfceditbrowsectrlenablebrowsebutton"></a><a name="enablebrowsebutton"></a>CMFCEdit 浏览Ctrl：：启用浏览按钮

显示或不在当前编辑浏览控件上显示浏览按钮。

```cpp
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>参数

*b 启用*<br/>
TRUE 显示浏览按钮;FALSE 不显示浏览按钮。 默认值为 TRUE。

*szLabel*<br/>
浏览按钮上显示的标签。 默认值为 **"..."。**

### <a name="remarks"></a>备注

如果*bEnable*参数为 TRUE，则实现自定义操作，以便在单击浏览按钮时执行。 要实现自定义操作，请从类派生一个`CMFCEditBrowseCtrl`类，然后重写其[OnBrowse](#onbrowse)方法。

如果*bEnable*参数为 TRUE，则控件的浏览模式`BrowseMode_Default`为 ;否则，浏览模式为`BrowseMode_None`。 有关浏览模式的详细信息，请参阅[GetMode](#getmode)方法。

## <a name="cmfceditbrowsectrlenablefilebrowsebutton"></a><a name="enablefilebrowsebutton"></a>CMFCEdit 浏览Ctrl：：启用文件浏览按钮

在当前编辑浏览控件上显示浏览按钮，并将控件置于*文件浏览*模式。

```cpp
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,
    LPCTSTR lpszFilter=NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```

### <a name="parameters"></a>参数

*lpszDefExt*<br/>
指定在文件选择对话框中使用的默认文件扩展名。 默认值为 NULL。

*lpszFilter*<br/>
指定在文件选择对话框中使用的默认筛选器字符串。 默认值为 NULL。

dwFlags**<br/>
对话框标志。 默认值是 OFN_HIDEREADONLY 和 OFN_OVERWRITEPROMPT 的按位组合 (OR)。

### <a name="remarks"></a>备注

当编辑浏览控件处于文件浏览模式，并且在用户单击浏览按钮时，该控件将显示标准文件选择对话框。

有关可用标志的完整列表，请参阅[OPENFILENAME 结构](/windows/win32/api/commdlg/ns-commdlg-openfilenamew)。

## <a name="cmfceditbrowsectrlenablefolderbrowsebutton"></a><a name="enablefolderbrowsebutton"></a>CMFCEdit 浏览Ctrl：：启用文件夹浏览按钮

在当前编辑浏览控件上显示浏览按钮，并将该控件置于*文件夹浏览*模式。

```cpp
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>备注

当编辑浏览控件处于文件夹浏览模式，并且用户单击浏览按钮时，该控件将显示标准文件夹选择对话框。

## <a name="cmfceditbrowsectrlgetmode"></a><a name="getmode"></a>CMFCEdit 浏览Ctrl：获取模式

检索当前编辑浏览控件的浏览模式。

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>返回值

指定编辑浏览控件的当前模式的枚举值之一。 浏览模式确定框架是否显示浏览按钮，以及当用户单击该按钮时将执行什么操作。

下表列出可能的返回值。

|“值”|说明|
|-----------|-----------------|
|`BrowseMode_Default`|**自定义模式**。 执行程序员定义的操作。|
|`BrowseMode_File`|**文件模式**. 将显示标准文件浏览器对话框。|
|`BrowseMode_Folder`|**文件夹模式**。 将显示标准文件夹浏览器对话框。|
|`BrowseMode_None`|不显示浏览按钮。|

### <a name="remarks"></a>备注

默认情况下，`CMFCEditBrowseCtrl`对象被初始化为`BrowseMode_None`模式。 使用[CMFCEditBrowseCtrl 修改浏览模式：：启用浏览按钮](#enablebrowsebutton)[、CMFCEditBrowseCtrl：：启用文件浏览按钮](#enablefilebrowsebutton)和[CMFCEditBrowseCtrl：：启用文件夹浏览按钮](#enablefolderbrowsebutton)方法。

## <a name="cmfceditbrowsectrlonafterupdate"></a><a name="onafterupdate"></a>CMFCEdit 浏览Ctrl：在更新后打开

编辑浏览控件使用浏览操作的结果更新后由框架调用。

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>备注

重写派生类中的此方法以实现自定义操作。

## <a name="cmfceditbrowsectrlonbrowse"></a><a name="onbrowse"></a>CMFCEdit 浏览Ctrl：：在浏览

用户单击编辑浏览控件的浏览按钮后由框架调用。

```
virtual void OnBrowse();
```

### <a name="remarks"></a>备注

当用户单击编辑浏览控件的浏览按钮时，使用此方法执行自定义代码。 从`CMFCEditBrowseCtrl`类派生您自己的类并重写其`OnBrowse`方法。 在该方法中，实现自定义浏览操作，并选择更新编辑浏览控件的文本框。 在应用程序中，使用[启用BrowseButton](#enablebrowsebutton)方法将编辑浏览控件置于*自定义浏览*模式。

## <a name="cmfceditbrowsectrlonchangelayout"></a><a name="onchangelayout"></a>CMFCEdit 浏览Ctrl：：在更改布局上

重绘当前编辑浏览控件。

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>备注

当编辑浏览控件的浏览模式发生更改时，框架将调用此方法。 有关详细信息，请参阅[CMFCEditBrowseCtrl：：获取模式](#getmode)。

## <a name="cmfceditbrowsectrlondrawbrowsebutton"></a><a name="ondrawbrowsebutton"></a>CMFCEdit 浏览Ctrl：：在绘制浏览按钮

框架调用以在编辑浏览控件上绘制浏览按钮。

```
virtual void OnDrawBrowseButton(
    CDC* pDC,
    CRect rect,
    BOOL bIsButtonPressed,
    BOOL bIsButtonHot);
```

### <a name="parameters"></a>参数

*pDC*<br/>
一个指向设备上下文的指针。

*矩形*<br/>
浏览按钮的边界矩形。

*bIsButton压榨*<br/>
如果按下按钮，则为 TRUE;否则，FALSE。

*bIsButtonHot*<br/>
如果按钮突出显示，则为 TRUE;如果按钮突出显示，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

在派生类中重写此函数以自定义浏览按钮的外观。

## <a name="cmfceditbrowsectrlsetbrowsebuttonimage"></a><a name="setbrowsebuttonimage"></a>CMFCEdit 浏览Ctrl：：设置浏览按钮图像

在编辑浏览控件的浏览按钮上设置自定义图像。

```cpp
void SetBrowseButtonImage(
    HICON hIcon,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(UINT uiBmpResId);
```

### <a name="parameters"></a>参数

*hIcon*<br/>
图标的句柄。

*hBitmap*<br/>
位图的句柄。

*乌布布雷西德*<br/>
位图的资源 ID。

*bAuto销毁*<br/>
TRUE 在此方法退出时删除指定的图标或位图;否则，FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

使用此方法将自定义图像应用于浏览按钮。 默认情况下，当编辑浏览控件处于*文件浏览*或*文件夹浏览*模式时，框架将获取标准图像。

## <a name="cmfceditbrowsectrlonillegalfilename"></a><a name="onillegalfilename"></a>CMFCEdit 浏览Ctrl：在非法文件名上

在编辑控件中输入非法文件名时由框架调用。

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>参数

*strFilename*<br/>
指定非法文件名。

### <a name="return-value"></a>返回值

如果无法将此文件名进一步传递到文件对话框，则应返回 FALSE。 在这种情况下，焦点将设置回编辑控件，用户应继续编辑。 默认实现显示一个消息框，告知用户非法文件名并返回 FALSE。 您可以重写此方法、更正文件名并返回 TRUE 以进行进一步处理。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
