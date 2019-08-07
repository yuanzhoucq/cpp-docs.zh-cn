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
ms.openlocfilehash: 31fadc0a960ddfcf216951e1af481983b122ea0f
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821313"
---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl 类

`CMFCEditBrowseCtrl`类支持编辑浏览控件, 该控件可选择包含浏览按钮的可编辑文本框。 当用户单击浏览按钮时，此控件会执行自定义操作或显示包含文件浏览器或文件夹浏览器的标准对话框。

## <a name="syntax"></a>语法

```
class CMFCEditBrowseCtrl : public CEdit
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|默认构造函数。|
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|启用或禁用 (隐藏) 浏览按钮。|
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|启用 "浏览" 按钮, 并将 "编辑浏览" 控件放在*文件浏览*模式下。|
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|启用 "浏览" 按钮, 并将 "编辑" 浏览控件置于*文件夹浏览*模式下。|
|[CMFCEditBrowseCtrl::GetMode](#getmode)|返回当前浏览模式。|
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|当使用浏览操作的结果更新编辑浏览控件之后, 由框架调用。|
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|用户单击 "浏览" 按钮后, 由框架调用。|
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|重绘当前的编辑浏览控件。|
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|由框架调用以绘制浏览按钮。|
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|当在编辑控件中输入非法文件名时由框架调用。|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|转换窗口消息, 然后将其调度到[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函数。 有关语法和详细信息, 请参阅[CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。|
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|为 "浏览" 按钮设置自定义图像。|

## <a name="remarks"></a>备注

使用 "编辑浏览" 控件选择文件或文件夹名称。 (可选) 使用控件执行自定义操作, 如以显示对话框。 可以显示或不显示 "浏览" 按钮, 也可以在按钮上应用自定义标签或图像。

编辑浏览控件的*浏览模式*确定它是否显示 "浏览" 按钮, 以及在单击按钮时执行的操作。 有关详细信息, 请参阅[GetMode](#getmode)方法。

`CMFCEditBrowseCtrl`类支持以下模式。

- **自定义模式**

   当用户单击 "浏览" 按钮时, 将执行自定义操作。 例如, 可以显示特定于应用程序的对话框。

- **文件模式**

   当用户单击 "浏览" 按钮时, 将显示 "标准文件选择" 对话框。

- **文件夹模式**

   当用户单击 "浏览" 按钮时, 将显示 "标准文件夹选择" 对话框。

## <a name="how-to-specify-an-edit-browse-control"></a>操作说明：指定编辑浏览控件

执行以下步骤以在应用程序中合并编辑浏览控件:

1. 如果要实现自定义浏览模式, 请从类派生你自己的`CMFCEditBrowseCtrl`类, 然后重写[CMFCEditBrowseCtrl:: OnBrowse](#onbrowse)方法。 在重写的方法中, 执行自定义浏览操作并使用结果更新 "编辑浏览" 控件。

1. 将`CMFCEditBrowseCtrl`对象或派生的编辑浏览控件对象嵌入父窗口对象。

1. 如果使用**类向导**创建对话框, 请将编辑控件 ( `CEdit`) 添加到对话框窗体。 此外, 添加一个变量以访问头文件中的控件。 在头文件中, 将变量的类型从`CEdit`更改为。 `CMFCEditBrowseCtrl` 将自动创建 "编辑" 浏览控件。 如果不使用**类向导**, 请将`CMFCEditBrowseCtrl`变量添加到头文件中, 然后调用其`Create`方法。

1. 如果向对话框添加 "编辑浏览" 控件, 请使用**ClassWizard**工具设置数据交换。

1. 调用[EnableFolderBrowseButton](#enablefolderbrowsebutton)、 [EnableFileBrowseButton](#enablefilebrowsebutton)或[EnableBrowseButton](#enablebrowsebutton)方法来设置浏览模式并显示 "浏览" 按钮。 调用[GetMode](#getmode)方法以获取当前浏览模式。

1. 若要为浏览按钮提供自定义映像, 请调用[SetBrowseButtonImage](#setbrowsebuttonimage)方法或重写[OnDrawBrowseButton](#ondrawbrowsebutton)方法。

1. 若要从编辑浏览控件中删除浏览按钮, 请调用[EnableBrowseButton](#enablebrowsebutton)方法, 并将*bEnable*参数设置为 FALSE。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>示例

下面的示例演示如何使用类中的`CMFCEditBrowseCtrl`两个方法: `EnableFolderBrowseButton`和。 `EnableFileBrowseButton` 此示例是[新控件示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>要求

**标头:** afxeditbrowsectrl

##  <a name="enablebrowsebutton"></a>CMFCEditBrowseCtrl:: EnableBrowseButton

显示或不显示当前编辑浏览控件上的浏览按钮。

```
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>参数

*bEnable*<br/>
如果显示 "浏览" 按钮, 则为 TRUE;FALSE 不显示 "浏览" 按钮。 默认值为 TRUE。

*szLabel*<br/>
"浏览" 按钮上显示的标签。 默认值为 " **...** "。

### <a name="remarks"></a>备注

如果*bEnable*参数为 TRUE, 则在单击 "浏览" 按钮时实现要执行的自定义操作。 若要实现自定义操作, 请从`CMFCEditBrowseCtrl`类派生一个类, 然后重写其[OnBrowse](#onbrowse)方法。

如果*bEnable*参数为 TRUE, 则控件`BrowseMode_Default`的浏览模式为; 否则, 浏览模式为。 `BrowseMode_None` 有关浏览模式的详细信息, 请参阅[GetMode](#getmode)方法。

##  <a name="enablefilebrowsebutton"></a>CMFCEditBrowseCtrl:: EnableFileBrowseButton

显示当前编辑浏览控件上的 "浏览" 按钮, 并将控件置于 "*文件浏览*" 模式。

```
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

*dwFlags*<br/>
对话框标志。 默认值是 OFN_HIDEREADONLY 和 OFN_OVERWRITEPROMPT 的按位组合 (OR)。

### <a name="remarks"></a>备注

当编辑浏览控件处于文件浏览模式，并且在用户单击浏览按钮时，该控件将显示标准文件选择对话框。

有关可用标志的完整列表, 请参阅[OPENFILENAME 结构](/windows/win32/api/commdlg/ns-commdlg-openfilenamew)。

##  <a name="enablefolderbrowsebutton"></a>CMFCEditBrowseCtrl:: EnableFolderBrowseButton

显示当前编辑浏览控件上的 "浏览" 按钮, 并将控件置于*文件夹浏览*模式中。

```
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>备注

当 "编辑浏览" 控件处于文件夹浏览模式并且用户单击 "浏览" 按钮时, 控件将显示 "标准文件夹选择" 对话框。

##  <a name="getmode"></a>CMFCEditBrowseCtrl:: GetMode

检索当前编辑浏览控件的浏览模式。

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>返回值

枚举值之一, 它指定编辑浏览控件的当前模式。 浏览模式确定框架是否显示 "浏览" 按钮, 以及用户单击该按钮时执行的操作。

下表列出可能的返回值。

|值|描述|
|-----------|-----------------|
|`BrowseMode_Default`|**自定义模式**。 执行程序员定义的操作。|
|`BrowseMode_File`|**文件模式**。 将显示 "标准文件浏览器" 对话框。|
|`BrowseMode_Folder`|**文件夹模式**。 将显示 "标准文件夹浏览器" 对话框。|
|`BrowseMode_None`|"浏览" 按钮不会显示。|

### <a name="remarks"></a>备注

默认情况下, `CMFCEditBrowseCtrl`对象初始化为`BrowseMode_None` mode。 用[CMFCEditBrowseCtrl:: EnableBrowseButton](#enablebrowsebutton)、 [CMFCEditBrowseCtrl:: EnableFileBrowseButton](#enablefilebrowsebutton)和[CMFCEditBrowseCtrl:: EnableFolderBrowseButton](#enablefolderbrowsebutton)方法修改浏览模式。

##  <a name="onafterupdate"></a>CMFCEditBrowseCtrl:: OnAfterUpdate

当使用浏览操作的结果更新编辑浏览控件之后, 由框架调用。

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>备注

在派生类中重写此方法以实现自定义操作。

##  <a name="onbrowse"></a>CMFCEditBrowseCtrl:: OnBrowse

当用户单击 "编辑浏览" 控件的 "浏览" 按钮后, 由框架调用。

```
virtual void OnBrowse();
```

### <a name="remarks"></a>备注

当用户单击 "编辑浏览" 控件的 "浏览" 按钮时, 使用此方法来执行自定义代码。 从类派生你自己的`CMFCEditBrowseCtrl`类并重写其`OnBrowse`方法。 在该方法中, 实现自定义浏览操作, 并根据需要更新 "编辑浏览" 控件的文本框。 在应用程序中, 使用[EnableBrowseButton](#enablebrowsebutton)方法将 "编辑浏览" 控件置于 "*自定义浏览*" 模式下。

##  <a name="onchangelayout"></a>CMFCEditBrowseCtrl:: OnChangeLayout

重绘当前的编辑浏览控件。

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>备注

编辑浏览器控件的浏览模式发生更改时, 框架会调用此方法。 有关详细信息, 请参阅[CMFCEditBrowseCtrl:: GetMode](#getmode)。

##  <a name="ondrawbrowsebutton"></a>CMFCEditBrowseCtrl:: OnDrawBrowseButton

由框架调用, 以在编辑浏览控件上绘制浏览按钮。

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
"浏览" 按钮的边框。

*bIsButtonPressed*<br/>
如果按下了按钮, 则为 TRUE;否则为 FALSE。

*bIsButtonHot*<br/>
如果按钮突出显示, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

在派生类中重写此函数, 以自定义浏览按钮的外观。

##  <a name="setbrowsebuttonimage"></a>CMFCEditBrowseCtrl:: SetBrowseButtonImage

在 "编辑浏览" 控件的 "浏览" 按钮上设置自定义图像。

```
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

*uiBmpResId*<br/>
位图的资源 ID。

*bAutoDestroy*<br/>
若要在此方法退出时删除指定的图标或位图, 则为 TRUE;否则为 FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

使用此方法可将自定义图像应用到浏览按钮。 默认情况下, 当编辑浏览控件处于*文件浏览*或*文件夹浏览*模式时, 框架将获取标准图像。

##  <a name="onillegalfilename"></a>  CMFCEditBrowseCtrl::OnIllegalFileName

当在编辑控件中输入非法文件名时由框架调用。

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>参数

*strFileName*<br/>
指定非法文件名。

### <a name="return-value"></a>返回值

如果无法将此文件名进一步传递到 file 对话框, 则应返回 FALSE。 在这种情况下, 焦点将返回到编辑控件, 用户应继续编辑。 默认实现将显示一个消息框, 该消息框向用户指示非法文件名并返回 FALSE。 您可以重写此方法, 更正文件名, 并返回 TRUE 以便进一步处理。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
