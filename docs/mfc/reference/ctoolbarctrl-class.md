---
title: "CToolBarCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CToolBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CToolBarCtrl class
- Windows common controls [C++], CToolBarCtrl
- toolbar controls [MFC], CToolBarCtrl class
- tool tips [C++], notifications
ms.assetid: 8f2f8ad2-05d7-4975-8715-3f2eed795248
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 2d3ec23d6147299d9a615e9edb0d3f90680bbfac
ms.lasthandoff: 02/24/2017

---
# <a name="ctoolbarctrl-class"></a>CToolBarCtrl 类
提供 Windows 工具栏公共控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CToolBarCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CToolBarCtrl::CToolBarCtrl](#ctoolbarctrl)|构造 `CToolBarCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CToolBarCtrl::AddBitmap](#addbitmap)|将一个或多个位图按钮图像添加到的可用于工具栏控件的按钮图像的列表。|  
|[CToolBarCtrl::AddButtons](#addbuttons)|向工具栏控件添加一个或多个按钮。|  
|[CToolBarCtrl::AddString](#addstring)|将添加一个新字符串，作为资源 ID，到工具栏的内部列表的字符串传递。|  
|[CToolBarCtrl::AddStrings](#addstrings)|添加一个新字符串或作为指针传递到 null 分隔的字符串，到工具栏的内部列表的字符串缓冲区的字符串。|  
|[CToolBarCtrl::AutoSize](#autosize)|调整工具栏控件的大小。|  
|[CToolBarCtrl::ChangeBitmap](#changebitmap)|更改当前的工具栏控件中的按钮的位图。|  
|[CToolBarCtrl::CheckButton](#checkbutton)|选中或清除给定的按钮在工具栏控件中。|  
|[CToolBarCtrl::CommandToIndex](#commandtoindex)|检索与指定的命令标识符关联的按钮的从零开始索引。|  
|[CToolBarCtrl::Create](#create)|创建工具栏控件，并将其附加到`CToolBarCtrl`对象。|  
|[CToolBarCtrl::CreateEx](#createex)|与指定的 Windows 扩展样式创建工具栏控件，并将其附加到`CToolBarCtrl`对象。|  
|[CToolBarCtrl::Customize](#customize)|显示自定义工具栏对话框。|  
|[CToolBarCtrl::DeleteButton](#deletebutton)|从工具栏控件中删除一个按钮。|  
|[CToolBarCtrl::EnableButton](#enablebutton)|启用或禁用工具栏控件中指定的按钮。|  
|[CToolBarCtrl::GetAnchorHighlight](#getanchorhighlight)|检索设置工具栏的定位点突出显示。|  
|[CToolBarCtrl::GetBitmap](#getbitmap)|检索相关联的按钮在工具栏中的位图的索引。|  
|[CToolBarCtrl::GetBitmapFlags](#getbitmapflags)|获取与工具栏的位图关联的标志。|  
|[CToolBarCtrl::GetButton](#getbutton)|检索有关指定的按钮在工具栏控件中的信息。|  
|[CToolBarCtrl::GetButtonCount](#getbuttoncount)|检索按钮工具栏控件中的当前计数。|  
|[CToolBarCtrl::GetButtonInfo](#getbuttoninfo)|检索一个按钮在工具栏中的信息。|  
|[CToolBarCtrl::GetButtonSize](#getbuttonsize)|检索当前的宽度和高度的工具栏按钮，以像素为单位。|  
|[CToolBarCtrl::GetColorScheme](#getcolorscheme)|检索当前的工具栏控件的配色方案。|  
|[CToolBarCtrl::GetDisabledImageList](#getdisabledimagelist)|检索到显示禁用按钮使用工具栏控件的图像列表。|  
|[CToolBarCtrl::GetDropTarget](#getdroptarget)|检索[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)工具栏控件的接口。|  
|[CToolBarCtrl::GetExtendedStyle](#getextendedstyle)|检索在工具栏控件的扩展的样式。|  
|[CToolBarCtrl::GetHotImageList](#gethotimagelist)|检索用于显示"热"按钮在工具栏控件的图像列表。 当鼠标指针位于其上方时突出显示热按钮。|  
|[CToolBarCtrl::GetHotItem](#gethotitem)|检索在工具栏中的热项的索引。|  
|[CToolBarCtrl::GetImageList](#getimagelist)|检索工具栏控件用于显示在其默认状态的按钮的图像列表。|  
|[CToolBarCtrl::GetInsertMark](#getinsertmark)|检索当前插入标记的工具栏。|  
|[CToolBarCtrl::GetInsertMarkColor](#getinsertmarkcolor)|检索用来绘制工具栏上的插入标记的颜色。|  
|[CToolBarCtrl::GetItemRect](#getitemrect)|检索工具栏控件中的按钮的边框。|  
|[CToolBarCtrl::GetMaxSize](#getmaxsize)|检索所有可见的按钮和工具栏中的分隔符的总大小。|  
|[CToolBarCtrl::GetMaxTextRows](#getmaxtextrows)|检索在工具栏按钮上显示的文本行的最大数目。|  
|[CToolBarCtrl::GetMetrics](#getmetrics)|检索工具栏控件的度量值。|  
|[CToolBarCtrl::GetPadding](#getpadding)|检索当前的工具栏控件的水平和垂直填充。|  
|[CToolBarCtrl::GetPressedImageList](#getpressedimagelist)|检索当前的工具栏控件使用以表示按钮处于按下状态的图像列表。|  
|[CToolBarCtrl::GetRect](#getrect)|检索指定的工具栏按钮的边框。|  
|[CToolBarCtrl::GetRows](#getrows)|检索当前显示在工具栏中的按钮的行数。|  
|[CToolBarCtrl::GetState](#getstate)|检索有关指定的按钮在工具栏控件中，例如操作是已启用、 按下，还是已检查的状态信息。|  
|[CToolBarCtrl::GetString](#getstring)|检索工具栏字符串。|  
|[CToolBarCtrl::GetStyle](#getstyle)|检索当前正在使用工具栏控件的样式。|  
|[CToolBarCtrl::GetToolTips](#gettooltips)|如果有的话关联工具栏控件中检索工具提示控件，句的柄。|  
|[CToolBarCtrl::HideButton](#hidebutton)|隐藏或显示指定的按钮在工具栏控件中。|  
|[CToolBarCtrl::HitTest](#hittest)|确定工具栏控件中的一个点所在。|  
|[CToolBarCtrl::Indeterminate](#indeterminate)|设置或清除指定按钮在工具栏控件中的不确定 （灰色） 状态。|  
|[CToolBarCtrl::InsertButton](#insertbutton)|在工具栏控件中插入一个按钮。|  
|[CToolBarCtrl::InsertMarkHitTest](#insertmarkhittest)|检索在工具栏中的点的插入标记信息。|  
|[CToolBarCtrl::IsButtonChecked](#isbuttonchecked)|指示是否已选中指定按钮在工具栏控件中。|  
|[CToolBarCtrl::IsButtonEnabled](#isbuttonenabled)|指示是否启用指定的按钮在工具栏控件中。|  
|[CToolBarCtrl::IsButtonHidden](#isbuttonhidden)|指示是否隐藏工具栏控件中指定的按钮。|  
|[CToolBarCtrl::IsButtonHighlighted](#isbuttonhighlighted)|检查工具栏按钮的突出显示状态。|  
|[CToolBarCtrl::IsButtonIndeterminate](#isbuttonindeterminate)|指示指定的按钮在工具栏控件中的状态是否是不确定 （灰色）。|  
|[CToolBarCtrl::IsButtonPressed](#isbuttonpressed)|指示是否按下工具栏控件中指定的按钮。|  
|[CToolBarCtrl::LoadImages](#loadimages)|将位图加载到工具栏控件的图像列表。|  
|[CToolBarCtrl::MapAccelerator](#mapaccelerator)|将一个加速器字符映射到一个工具栏按钮。|  
|[CToolBarCtrl::MarkButton](#markbutton)|在工具栏控件中设置给定的按钮的突出显示状态。|  
|[CToolBarCtrl::MoveButton](#movebutton)|将一个按钮从一个索引移到另一个。|  
|[CToolBarCtrl::PressButton](#pressbutton)|按下或释放在工具栏控件中指定的按钮。|  
|[CToolBarCtrl::ReplaceBitmap](#replacebitmap)|用新位图替换当前的工具栏控件中现有的位图。|  
|[CToolBarCtrl::RestoreState](#restorestate)|还原工具栏控件的状态。|  
|[CToolBarCtrl::SaveState](#savestate)|保存工具栏控件的状态。|  
|[CToolBarCtrl::SetAnchorHighlight](#setanchorhighlight)|设置设置为工具栏的定位点突出显示。|  
|[CToolBarCtrl::SetBitmapSize](#setbitmapsize)|设置要添加到工具栏控件的位图化图像的大小。|  
|[CToolBarCtrl::SetButtonInfo](#setbuttoninfo)|在工具栏中设置的现有按钮的信息。|  
|[CToolBarCtrl::SetButtonSize](#setbuttonsize)|设置要添加到工具栏控件的按钮的大小。|  
|[CToolBarCtrl::SetButtonStructSize](#setbuttonstructsize)|指定的大小`TBBUTTON`结构。|  
|[CToolBarCtrl::SetButtonWidth](#setbuttonwidth)|在工具栏控件中设置的最小值和最大按钮的宽度。|  
|[CToolBarCtrl::SetCmdID](#setcmdid)|设置要发送到所有者窗口中，按指定的按钮时的命令标识符。|  
|[CToolBarCtrl::SetColorScheme](#setcolorscheme)|设置当前的工具栏控件的配色方案。|  
|[CToolBarCtrl::SetDisabledImageList](#setdisabledimagelist)|将工具栏控件将使用的图像列表设置为显示禁用按钮。|  
|[CToolBarCtrl::SetDrawTextFlags](#setdrawtextflags)|Win32 函数中设置的标志[DrawText](http://msdn.microsoft.com/library/windows/desktop/dd162498)，用于按照如何设置的标志设置格式的指定矩形中绘制文本。|  
|[CToolBarCtrl::SetExtendedStyle](#setextendedstyle)|设置工具栏控件的扩展的样式。|  
|[CToolBarCtrl::SetHotImageList](#sethotimagelist)|设置工具栏控件将用于显示"热"按钮的图像列表。|  
|[CToolBarCtrl::SetHotItem](#sethotitem)|在工具栏中设置的热的项。|  
|[CToolBarCtrl::SetImageList](#setimagelist)|设置工具栏上将用来显示它们的默认状态的按钮的图像列表。|  
|[CToolBarCtrl::SetIndent](#setindent)|设置工具栏控件中的第一个按钮的缩进。|  
|[CToolBarCtrl::SetInsertMark](#setinsertmark)|设置工具栏上的当前插入标记。|  
|[CToolBarCtrl::SetInsertMarkColor](#setinsertmarkcolor)|设置用于绘制工具栏上的插入标记的颜色。|  
|[CToolBarCtrl::SetMaxTextRows](#setmaxtextrows)|设置最大工具栏按钮上显示的文本行数。|  
|[CToolBarCtrl::SetMetrics](#setmetrics)|设置工具栏控件的度量值。|  
|[CToolBarCtrl::SetOwner](#setowner)|设置窗口以接收来自工具栏控件通知消息。|  
|[CToolBarCtrl::SetPadding](#setpadding)|设置当前的工具栏控件的水平和垂直填充。|  
|[CToolBarCtrl::SetPressedImageList](#setpressedimagelist)|设置当前的工具栏控件使用以表示按钮处于按下状态的图像列表。|  
|[CToolBarCtrl::SetRows](#setrows)|设置按钮的工具栏中显示的行数。|  
|[CToolBarCtrl::SetState](#setstate)|在工具栏控件中设置指定按钮的状态。|  
|[CToolBarCtrl::SetStyle](#setstyle)|设置工具栏控件的样式。|  
|[CToolBarCtrl::SetToolTips](#settooltips)|将工具提示控件与工具栏控件相关联。|  
|[CToolBarCtrl::SetWindowTheme](#setwindowtheme)|设置工具栏控件的视觉样式。|  
  
## <a name="remarks"></a>备注  
 此控件 (并因此`CToolBarCtrl`类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 Windows 工具栏公共控件是包含一个或多个按钮的矩形的子窗口。 这些按钮可以显示的位图图像，一个字符串，或这两者。 当用户选择一个按钮时，它向工具栏的所有者窗口发送一条命令消息。 通常情况下，在工具栏中的按钮对应于应用程序的菜单项它们提供更直接的方式来访问应用程序的命令的用户。  
  
 `CToolBarCtrl`对象包含几个重要的内部数据结构︰ 列表按钮图像位图或图像列表、 按钮标签字符串的列表和一份`TBBUTTON`结构中将一个图像关联和/或字符串的位置，样式，该结构状态，并且命令按钮的 ID。 每种数据结构的元素称为按从零开始的索引。 然后才能使用`CToolBarCtrl`对象时，您必须设置这些数据结构。 字符串的列表可以仅用于按钮标签;无法从工具栏中检索字符串。  
  
 为了使用 `CToolBarCtrl` 对象，您通常将执行下列步骤：  
  
1.  构造 `CToolBarCtrl` 对象。  
  
2.  调用[创建](#create)创建 Windows 工具栏公共控件并将其附加到`CToolBarCtrl`对象。 通过使用样式，如指示工具栏样式的**TBSTYLE_TRANSPARENT**透明工具栏或**TBSTYLE_DROPDOWN**对于支持下拉列表样式按钮的工具栏。  
  
3.  确定要如何显示工具栏上的按钮︰  
  
    -   若要使用位图图像按钮，按钮位图向工具栏添加通过调用[AddBitmap](#addbitmap)。  
  
    -   若要使用图像列表中的按钮显示图像，通过调用指定的图像列表[SetImageList](#setimagelist)， [SetHotImageList](#sethotimagelist)，或[SetDisabledImageList](#setdisabledimagelist)。  
  
    -   若要使用按钮字符串标签，将字符串添加到工具栏通过调用[AddString](#addstring)和/或[AddStrings](#addstrings)。  
  
4.  通过调用添加到工具栏的按钮结构[AddButtons](#addbuttons)。  
  
5.  如果希望工具提示中不是所有者窗口的工具栏按钮`CFrameWnd`，您需要处理**TTN_NEEDTEXT**工具栏的所有者窗口中的邮件数中所述[处理工具提示通知](../../mfc/handling-tool-tip-notifications.md)。 如果工具栏上的父窗口派生自`CFrameWnd`，工具提示显示而无需从您任何额外工作，因为`CFrameWnd`提供默认处理程序。  
  
6.  如果您想让用户能够自定义工具栏，处理是所有者窗口中的自定义通知消息中所述[处理自定义通知](../../mfc/handling-customization-notifications.md)。  
  
 您可以使用[SaveState](#savestate)将工具栏控件的当前状态保存在注册表和[RestoreState](#restorestate)还原根据信息存储在注册表中以前的状态。 除了节省之外之间使用的应用程序的工具栏状态，应用程序通常存储状态之前用户开始自定义工具栏，以防用户稍后想要将工具栏还原到其原始状态。  
  
## <a name="support-for-internet-explorer-version-40-and-later"></a>对 Internet Explorer 版本 4.0 和更高版本的支持  
 若要支持在 Internet Explorer 4.0 和更高版本，版本引入的功能 MFC 提供了图像列表支持和透明的并且平面样式工具栏上的控件。  
  
 透明工具栏允许下工具栏上的客户端显示出来。 要创建透明工具栏，请同时使用**TBSTYLE_FLAT**和**TBSTYLE_TRANSPARENT**样式。 透明工具栏功能热跟踪;也就是说，当鼠标指针移动作用按钮上方的工具栏上，该按钮的外观会发生变化。 使用创建的工具栏不仅仅是**TBSTYLE_FLAT**样式将包含按钮都是不透明的。  
  
 图像列表支持允许的默认行为、 热图像和禁用的图像控件更大的灵活性。 使用[GetImageList](#getimagelist)， [GetHotImageList](#gethotimagelist)，和[GetDisabledImageList](#getdisabledimagelist)与此操作根据其状态图像的透明工具栏︰  
  
 有关详细信息使用`CToolBarCtrl`，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CToolBarCtrl](../../mfc/using-ctoolbarctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CToolBarCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="a-nameaddbitmapa--ctoolbarctrladdbitmap"></a><a name="addbitmap"></a>CToolBarCtrl::AddBitmap  
 将一个或多个按钮图像添加到的存储在该工具栏控件的按钮图像的列表。  
  
```  
int AddBitmap(
    int nNumButtons,  
    UINT nBitmapID);

 
int AddBitmap(
    int nNumButtons,  
    CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>参数  
 `nNumButtons`  
 按钮图像位图中的数。  
  
 `nBitmapID`  
 包含要添加的按钮图像的位图资源标识符。  
  
 `pBitmap`  
 指向`CBitmap`对象，其中包含要添加的按钮图像。  
  
### <a name="return-value"></a>返回值  
 如果成功，则第一个新图像的从零开始的索引否则为-1。  
  
### <a name="remarks"></a>备注  
 您可以使用 Windows API [CreateMappedBitmap](http://msdn.microsoft.com/library/windows/desktop/bb787467)将位图添加到工具栏之前映射的颜色。 如果您将指针传递至**CBitMap**对象时，必须确保销毁工具栏后，该位图不销毁之前。  
  
##  <a name="a-nameaddbuttonsa--ctoolbarctrladdbuttons"></a><a name="addbuttons"></a>CToolBarCtrl::AddButtons  
 向工具栏控件添加一个或多个按钮。  
  
```  
BOOL AddButtons(
    int nNumButtons,  
    LPTBBUTTON lpButtons);
```  
  
### <a name="parameters"></a>参数  
 `nNumButtons`  
 要添加的按钮数。  
  
 `lpButtons`  
 数组的地址`TBBUTTON`包含有关要添加的按钮的信息的结构。 必须为指定按钮相同的数组中的元素数`nNumButtons`。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 `lpButtons`指针指向数组的`TBBUTTON`结构。 每个`TBBUTTON`结构将该按钮的样式、 图像和/或字符串，命令 ID、 状态和用户定义数据与正在添加的按钮相关联︰  
  
 `typedef struct _TBBUTTON {`  
  
 `int iBitmap;// zero-based index of button image`  
  
 `int idCommand;  // command to be sent when button pressed`  
  
 `BYTE fsState;   // button state--see below`  
  
 `BYTE fsStyle;   // button style--see below`  
  
 `DWORD dwData;   // application-defined value`  
  
 `int iString;// zero-based index of button label string`  
  
 `} TBBUTTON;`  
  
 成员是，如下所示︰  
  
 **iBitmap**  
 按钮图像，如果此按钮没有图像的从零开始索引。  
  
 **idCommand**  
 与该按钮关联的命令标识符。 此标识符会发送**WM_COMMAND**消息时则选择该按钮。 如果**fsStyle**成员都有`TBSTYLE_SEP`值，此成员必须为零。  
  
 **fsState**  
 按钮状态标志。 它可以是下面列出的值的组合︰  
  
- `TBSTATE_CHECKED`该按钮具有**TBSTYLE_CHECKED**样式，是否已按下。  
  
- `TBSTATE_ENABLED`按钮接受用户输入。 不具有此状态的按钮不接受用户输入，并显示为灰色。  
  
- `TBSTATE_HIDDEN`按钮不可见，并且不能接受用户输入。  
  
- `TBSTATE_INDETERMINATE`按钮为灰色。  
  
- `TBSTATE_PRESSED`按下了按钮。  
  
- `TBSTATE_WRAP`按钮后跟换行符。 此外必须具有按钮`TBSTATE_ENABLED`状态。  
  
 **fsStyle**  
 按钮样式。 它可以是下面列出的值的组合︰  
  
- `TBSTYLE_BUTTON`创建一个标准的推送按钮。  
  
- `TBSTYLE_CHECK`创建一个在用户单击它每次按下和未按下状态之间切换的按钮。 该按钮处于按下状态时具有不同的背景色。  
  
- `TBSTYLE_CHECKGROUP`创建一个将保持按下，直到按下的组中的另一个按钮的复选按钮。  
  
- `TBSTYLE_GROUP`创建一个将保持按下，直到按下的组中的另一个按钮的按钮。  
  
- `TBSTYLE_SEP`创建提供稍微按钮组之间的分隔符。 具有此样式时的按钮不会收到用户输入。  
  
 `dwData`  
 用户定义的数据。  
  
 **iString**  
 要使用作为按钮的字符串的从零开始的索引的标签，则此按钮没有字符串是否为-1。  
  
 使用图像和/或您提供其索引以前必须已添加到工具栏控件的字符串列出[AddBitmap](#addbitmap)， [AddString](#addstring)，和/或[AddStrings](#addstrings)。  
  
##  <a name="a-nameaddstringa--ctoolbarctrladdstring"></a><a name="addstring"></a>CToolBarCtrl::AddString  
 将添加一个新字符串，作为资源 ID，到工具栏的内部列表的字符串传递。  
  
```  
int AddString(UINT nStringID);
```  
  
### <a name="parameters"></a>参数  
 *nStringID*  
 若要添加到工具栏控件的字符串列表的字符串资源的资源标识符。  
  
### <a name="return-value"></a>返回值  
 如果成功，则添加的第一个新字符串的从零开始的索引否则为-1。  
  
##  <a name="a-nameaddstringsa--ctoolbarctrladdstrings"></a><a name="addstrings"></a>CToolBarCtrl::AddStrings  
 字符串可用于工具栏控件的列表中添加一个新字符串。  
  
```  
int AddStrings(LPCTSTR lpszStrings);
```  
  
### <a name="parameters"></a>参数  
 *lpszStrings*  
 包含要添加到工具栏的字符串列表中的一个或多个 null 值结束字符串的缓冲区地址。 最后一个的字符串必须包含两个 null 字符结尾。  
  
### <a name="return-value"></a>返回值  
 如果成功，则添加的第一个新字符串的从零开始的索引否则为-1。  
  
### <a name="remarks"></a>备注  
 必须由 null 字符分隔字符串缓冲区中。 您必须确保最后一个字符串具有两个 null 终止符。 若要正确设置为常量字符串的格式，可编写为︰  
  
 [!code-cpp[NVC_MFCControlLadenDialog #&72;](../../mfc/codesnippet/cpp/ctoolbarctrl-class_1.cpp)]  
  
 或：  
  
 [!code-cpp[NVC_MFCControlLadenDialog #&73;](../../mfc/codesnippet/cpp/ctoolbarctrl-class_2.cpp)]  
  
 您不应传递`CString`对象传递给此函数，因为它不是中可能有多个 null 字符`CString`。  
  
##  <a name="a-nameautosizea--ctoolbarctrlautosize"></a><a name="autosize"></a>CToolBarCtrl::AutoSize  
 调整整个工具栏控件的大小。  
  
```  
void AutoSize();
```  
  
### <a name="remarks"></a>备注  
 当父窗口的大小发生更改或工具栏的大小更改 （例如当您设置按钮或位图的大小，或将字符串添加） 时，应调用此函数。  
  
##  <a name="a-namechangebitmapa--ctoolbarctrlchangebitmap"></a><a name="changebitmap"></a>CToolBarCtrl::ChangeBitmap  
 更改当前的工具栏控件中的按钮的位图。  
  
```  
BOOL ChangeBitmap(
    int idButton,   
    int iBitmap);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `idButton`|要接收新位图的按钮的命令标识符。|  
|[in] `iBitmap`|当前工具栏控件的图像列表中的图像的从零开始索引。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 如果此方法成功，系统会显示在指定按钮中指定的图像。  
  
 此方法可发送[TB_CHANGEBITMAP](http://msdn.microsoft.com/library/windows/desktop/bb787301)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例将更改的位图**文件保存**的位图按钮**有关**按钮。  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctoolbarctrl-class_3.cpp)]  
  
##  <a name="a-namecheckbuttona--ctoolbarctrlcheckbutton"></a><a name="checkbutton"></a>CToolBarCtrl::CheckButton  
 选中或清除给定的按钮在工具栏控件中。  
  
```  
BOOL CheckButton(
    int nID,  
    BOOL bCheck = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 选中或清除按钮的命令标识符。  
  
 *bCheck*  
 **TRUE**检查按钮， **FALSE**以将其清除。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 当已选中一个按钮时，它似乎按下了。 如果您想要更改多个按钮的状态，请考虑调用[SetState](#setstate)相反。  
  
##  <a name="a-namecommandtoindexa--ctoolbarctrlcommandtoindex"></a><a name="commandtoindex"></a>CToolBarCtrl::CommandToIndex  
 检索与指定的命令标识符关联的按钮的从零开始索引。  
  
```  
UINT CommandToIndex(UINT nID) const;  
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 命令 ID 的按钮索引您想要查找。  
  
### <a name="return-value"></a>返回值  
 与命令 id。 关联的按钮的从零开始的索引  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namecreatea--ctoolbarctrlcreate"></a><a name="create"></a>CToolBarCtrl::Create  
 创建工具栏控件，并将其附加到`CToolBarCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定工具栏控件的样式。 必须始终具有工具栏**WS_CHILD**样式。 此外，可以指定工具栏样式和窗口样式的任意组合，如下所述**备注**。  
  
 `rect`  
 （可选） 指定工具栏控件的大小和位置。 它可为[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。  
  
 `pParentWnd`  
 指定工具栏控件的父窗口。 它不能**NULL**。  
  
 `nID`  
 指定工具栏控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 您构造`CToolBarCtrl`分两个步骤。 首先，调用构造函数中，，然后调用**创建**，它创建工具栏控件并将其附加到`CToolBarCtrl`对象。 向工具栏控件中应用下面的窗口样式。  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
 请参阅[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关窗口样式的说明。  
  
 （可选） 将应用的组合[常见控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775498)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 将工具栏样式的组合应用于控件或按钮本身。 主题中描述了样式[工具栏控件和按钮样式](http://msdn.microsoft.com/library/windows/desktop/bb760439)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 若要使用扩展的工具栏样式，请调用[SetExtendedStyle](#setextendedstyle)调用后**创建**。 若要创建包含扩展的窗口样式的工具栏，调用[CToolBarCtrl::CreateEx](#createex)而不是**创建**。  
  
 工具栏控件自动设置的大小和位置工具栏窗口中。 高度取决于在工具栏按钮的高度。 宽度是与父窗口工作区的宽度相同。 `CCS_TOP`和`CCS_BOTTOM`样式可确定是否沿顶部或底部的客户端区域放置工具栏。 默认情况下，工具栏包含`CCS_TOP`样式。  
  
##  <a name="a-namecreateexa--ctoolbarctrlcreateex"></a><a name="createex"></a>CToolBarCtrl::CreateEx  
 创建控件 （子窗口），并将其与相关联`CToolBarCtrl`对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwExStyle`  
 指定要创建的控件的扩展的样式。 扩展窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定工具栏控件的样式。 必须始终具有工具栏**WS_CHILD**样式。 此外，可以指定工具栏样式和窗口样式的任意组合，如中所述**备注**部分[创建](#create)。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口，在中创建的工作区坐标位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是[创建](#create)应用扩展的窗口样式、 指定的 Windows 扩展的样式前言**WS_EX_**。 **CreateEx**创建具有指定的扩展窗口样式控件`dwExStyle`。 设置扩展样式特定于控件使用[SetExtendedStyle](#setextendedstyle)。 例如，使用`CreateEx`设置作为此类样式**WS_EX_CONTEXTHELP**，但使用`SetExtendedStyle`设置作为此类样式**TBSTYLE_EX_DRAWDDARROWS**。 有关详细信息，请参阅中所述的样式[工具栏扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb760430)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namectoolbarctrla--ctoolbarctrlctoolbarctrl"></a><a name="ctoolbarctrl"></a>CToolBarCtrl::CToolBarCtrl  
 构造 `CToolBarCtrl` 对象。  
  
```  
CToolBarCtrl();
```  
  
### <a name="remarks"></a>备注  
 必须调用[创建](#create)以使工具栏上可用。  
  
##  <a name="a-namecustomizea--ctoolbarctrlcustomize"></a><a name="customize"></a>CToolBarCtrl::Customize  
 显示自定义工具栏对话框。  
  
```  
void Customize();
```  
  
### <a name="remarks"></a>备注  
 此对话框中，用户可以通过添加和删除按钮自定义工具栏。 若要支持自定义，工具栏的父窗口必须处理自定义通知消息中所述[处理自定义通知](../../mfc/handling-customization-notifications.md)。 您的工具栏上也必须已创建与`CCS_ADJUSTABLE`样式，如中所述[CToolBarCtrl::Create](#create)。  
  
 有关详细信息，请参阅知识库文章 Q241850: PRB︰ 号召 CToolBarCtrl::Customize 不会保留自定义对话框可见。  
  
##  <a name="a-namedeletebuttona--ctoolbarctrldeletebutton"></a><a name="deletebutton"></a>CToolBarCtrl::DeleteButton  
 从工具栏控件中删除一个按钮。  
  
```  
BOOL DeleteButton(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 删除按钮的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameenablebuttona--ctoolbarctrlenablebutton"></a><a name="enablebutton"></a>CToolBarCtrl::EnableButton  
 启用或禁用工具栏控件中指定的按钮。  
  
```  
BOOL EnableButton(
    int nID,  
    BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 若要启用或禁用该按钮的命令标识符。  
  
 `bEnable`  
 **TRUE**启用该按钮;**FALSE**禁用该按钮。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 当启用了一个按钮时，它可以按下和检查。 如果您想要更改多个按钮的状态，请考虑调用[SetState](#setstate)相反。  
  
##  <a name="a-namegetanchorhighlighta--ctoolbarctrlgetanchorhighlight"></a><a name="getanchorhighlight"></a>CToolBarCtrl::GetAnchorHighlight  
 检索设置工具栏的定位点突出显示。  
  
```  
BOOL GetAnchorHighlight() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果非零值，则启用定位点突出显示。 如果为零，定位点突出显示被禁用。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_GETANCHORHIGHLIGHT](http://msdn.microsoft.com/library/windows/desktop/bb787313)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetbitmapa--ctoolbarctrlgetbitmap"></a><a name="getbitmap"></a>CToolBarCtrl::GetBitmap  
 检索相关联的按钮在工具栏中的位图的索引。  
  
```  
int GetBitmap(int nID) const;  
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 其位图索引是要检索的按钮的命令标识符。  
  
### <a name="return-value"></a>返回值  
 返回的位图，如果成功，否则为零的索引。  
  
### <a name="remarks"></a>备注  
 实现的功能[TB_GETBITMAP](http://msdn.microsoft.com/library/windows/desktop/bb787315)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetbitmapflagsa--ctoolbarctrlgetbitmapflags"></a><a name="getbitmapflags"></a>CToolBarCtrl::GetBitmapFlags  
 检索从工具栏的位图标志。  
  
```  
UINT GetBitmapFlags() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**UINT**具有**TBBF_LARGE**设置标志，如果显示可以清除否则支持大型工具栏位图。  
  
### <a name="remarks"></a>备注  
 创建工具栏之后、 之前添加到工具栏的位图，不应调用它。 返回值指示是否显示是否支持大型位图。 如果显示器支持大型位图，并选择要使用它们，请调用[SetBitmapSize](#setbitmapsize)和[SetButtonSize](#setbuttonsize)然后再添加您大位图使用[AddBitmap](#addbitmap)。  
  
##  <a name="a-namegetbuttona--ctoolbarctrlgetbutton"></a><a name="getbutton"></a>CToolBarCtrl::GetButton  
 检索有关指定的按钮在工具栏控件中的信息。  
  
```  
BOOL GetButton(
    int nIndex,  
    LPTBBUTTON lpButton) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要为其检索信息的按钮的从零开始索引。  
  
 `lpButton`  
 地址的指针`TBBUTTON`结构，它是要接收的按钮信息的副本。 请参阅[CToolBarCtrl::AddButtons](#addbuttons)有关的信息`TBBUTTON`结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
##  <a name="a-namegetbuttoncounta--ctoolbarctrlgetbuttoncount"></a><a name="getbuttoncount"></a>CToolBarCtrl::GetButtonCount  
 检索按钮工具栏控件中的当前计数。  
  
```  
int GetButtonCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 这些按钮的计数。  
  
##  <a name="a-namegetbuttoninfoa--ctoolbarctrlgetbuttoninfo"></a><a name="getbuttoninfo"></a>CToolBarCtrl::GetButtonInfo  
 检索一个按钮在工具栏中的信息。  
  
```  
int GetButtonInfo(
    int nID,  
    TBBUTTONINFO* ptbbi) const;  
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 按钮标识符。  
  
 `ptbbi`  
 一个指向[TBBUTTONINFO](http://msdn.microsoft.com/library/windows/desktop/bb760478)接收按钮信息的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则按钮的从零开始的索引否则为-1。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_GETBUTTONINFO](http://msdn.microsoft.com/library/windows/desktop/bb787321)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetbuttonsizea--ctoolbarctrlgetbuttonsize"></a><a name="getbuttonsize"></a>CToolBarCtrl::GetButtonSize  
 获取一个工具栏按钮的大小。  
  
```  
DWORD GetButtonSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`DWORD`分别包含在 LOWORD 和 HIWORD，宽度和高度值的值。  
  
##  <a name="a-namegetbuttontexta--ctoolbarctrlgetbuttontext"></a><a name="getbuttontext"></a>CToolBarCtrl::GetButtonText  
 检索当前的工具栏控件上的指定按钮的显示文本。  
  
```  
CString GetButtonText(int idButton) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `idButton`|检索其显示文本的按钮的标识符。|  
  
### <a name="return-value"></a>返回值  
 一个[CString](../../atl-mfc-shared/using-cstring.md) ，其中包含指定的按钮的显示文本。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TB_GETBUTTONTEXT](http://msdn.microsoft.com/library/windows/desktop/bb787325)邮件中，Windows SDK 中所述。  
  
##  <a name="a-namegetcolorschemea--ctoolbarctrlgetcolorscheme"></a><a name="getcolorscheme"></a>CToolBarCtrl::GetColorScheme  
 检索当前的工具栏控件的配色方案。  
  
```  
BOOL GetColorScheme(COLORSCHEME* lpColorScheme) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[out] `lpColorScheme`|指向[要添加的配色](http://msdn.microsoft.com/library/windows/desktop/bb775502)结构，它接收的颜色方案信息。 此方法返回时，该结构描述的突出显示颜色和阴影颜色工具栏控件。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TB_GETCOLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb787327)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetdisabledimagelista--ctoolbarctrlgetdisabledimagelist"></a><a name="getdisabledimagelist"></a>CToolBarCtrl::GetDisabledImageList  
 检索到显示禁用按钮使用工具栏控件的图像列表。  
  
```  
CImageList* GetDisabledImageList() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CImageList](../../mfc/reference/cimagelist-class.md)对象，或**NULL**如果没有禁用的图像列表设置。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_GETDISABLEDIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787329)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 MFC 实现`GetDisabledImageList`使用`CImageList`对象，包含工具栏控件的按钮映像，而不是图像列表的句柄。  
  
##  <a name="a-namegetdroptargeta--ctoolbarctrlgetdroptarget"></a><a name="getdroptarget"></a>CToolBarCtrl::GetDropTarget  
 检索[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)工具栏控件的接口。  
  
```  
HRESULT GetDropTarget(IDropTarget** ppDropTarget) const;  
```  
  
### <a name="parameters"></a>参数  
 `ppDropTarget`  
 一个指向[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)接口指针。 如果发生错误， **NULL**指针放在此地址。  
  
### <a name="return-value"></a>返回值  
 返回`HRESULT`值，该值指示成功或失败的操作。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_GETOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787343)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetextendedstylea--ctoolbarctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CToolBarCtrl::GetExtendedStyle  
 检索在工具栏控件的扩展的样式。  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`DWORD`，表示当前正在使用工具栏控件的扩展的样式。 有关样式的列表，请参阅[工具栏扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb760430)，请在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb787331)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegethotimagelista--ctoolbarctrlgethotimagelist"></a><a name="gethotimagelist"></a>CToolBarCtrl::GetHotImageList  
 检索用于显示"热"按钮在工具栏控件的图像列表。 当鼠标指针位于其上方时突出显示热按钮。  
  
```  
CImageList* GetHotImageList() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CImageList](../../mfc/reference/cimagelist-class.md)对象，或**NULL**如果没有禁用的图像列表设置。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_GETHOTIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787334)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 当鼠标指针位于其上方时突出显示热按钮。  
  
##  <a name="a-namegethotitema--ctoolbarctrlgethotitem"></a><a name="gethotitem"></a>CToolBarCtrl::GetHotItem  
 检索在工具栏中的热项的索引。  
  
```  
int GetHotItem() const;  
```  
  
### <a name="return-value"></a>返回值  
 在工具栏中的热项的从零开始的索引。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_GETHOTITEM](http://msdn.microsoft.com/library/windows/desktop/bb787336)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetimagelista--ctoolbarctrlgetimagelist"></a><a name="getimagelist"></a>CToolBarCtrl::GetImageList  
 检索工具栏控件用于显示在其默认状态的按钮的图像列表。  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CImageList](../../mfc/reference/cimagelist-class.md)对象，或**NULL**如果不设置任何图像列表。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_GETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787337)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetinsertmarka--ctoolbarctrlgetinsertmark"></a><a name="getinsertmark"></a>CToolBarCtrl::GetInsertMark  
 检索当前插入标记的工具栏。  
  
```  
void GetInsertMark(TBINSERTMARK* ptbim) const;  
```  
  
### <a name="parameters"></a>参数  
 `ptbim`  
 一个指向[TBINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb760480)接收插入标记的结构。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_GETINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb787338)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetinsertmarkcolora--ctoolbarctrlgetinsertmarkcolor"></a><a name="getinsertmarkcolor"></a>CToolBarCtrl::GetInsertMarkColor  
 检索用来绘制工具栏上的插入标记的颜色。  
  
```  
COLORREF GetInsertMarkColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**COLORREF**值，该值包含当前插入标记颜色。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_GETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb787339)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetitemrecta--ctoolbarctrlgetitemrect"></a><a name="getitemrect"></a>CToolBarCtrl::GetItemRect  
 检索工具栏控件中的按钮的边框。  
  
```  
BOOL GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要为其检索信息的按钮的从零开始索引。  
  
 `lpRect`  
 地址的指针[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它接收的边框的坐标。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 此函数不会检索其状态设置为的按钮的边框`TBSTATE_HIDDEN`。  
  
##  <a name="a-namegetmaxsizea--ctoolbarctrlgetmaxsize"></a><a name="getmaxsize"></a>CToolBarCtrl::GetMaxSize  
 检索所有可见的按钮和工具栏中的分隔符的总大小。  
  
```  
BOOL GetMaxSize(LPSIZE pSize) const;  
```  
  
### <a name="parameters"></a>参数  
 `pSize`  
 一个指向[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构，它接收的项的大小。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_GETMAXSIZE](http://msdn.microsoft.com/library/windows/desktop/bb787341)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetmaxtextrowsa--ctoolbarctrlgetmaxtextrows"></a><a name="getmaxtextrows"></a>CToolBarCtrl::GetMaxTextRows  
 检索在工具栏按钮上显示的文本行的最大数目。  
  
```  
int GetMaxTextRows() const;  
```  
  
### <a name="return-value"></a>返回值  
 最大工具栏按钮上显示的文本行数。  
  
##  <a name="a-namegetmetricsa--ctoolbarctrlgetmetrics"></a><a name="getmetrics"></a>CToolBarCtrl::GetMetrics  
 检索的度量值`CToolBarCtrl`对象。  
  
```  
void GetMetrics(LPTBMETRICS ptbm) const;  
```  
  
### <a name="parameters"></a>参数  
 `ptbm`  
 一个指向[TBMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb760482)结构`CToolBarCtrl`对象。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[TB_GETMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb787342)消息，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetpaddinga--ctoolbarctrlgetpadding"></a><a name="getpadding"></a>CToolBarCtrl::GetPadding  
 检索当前的工具栏控件的水平和垂直填充。  
  
```  
BOOL GetPadding(
    int* pnHorzPadding,   
    int* pnVertPadding) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[out] `pnHorzPadding`|一个整数，以像素为单位接收工具栏控件的水平边距。|  
|[out] `pnVertPadding`|一个整数，以像素为单位接收工具栏控件的垂直边距。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TB_GETPADDING](http://msdn.microsoft.com/library/windows/desktop/bb787344)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetpressedimagelista--ctoolbarctrlgetpressedimagelist"></a><a name="getpressedimagelist"></a>CToolBarCtrl::GetPressedImageList  
 检索当前的工具栏控件使用以表示按钮处于按下状态的图像列表。  
  
```  
CImageList* GetPressedImageList();
```  
  
### <a name="return-value"></a>返回值  
 指向[CImageList](../../mfc/reference/cimagelist-class.md) ，其中包含当前控件的图像列表或`NULL`如果任何此类图像列表不设置。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TB_GETPRESSEDIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787345)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetrecta--ctoolbarctrlgetrect"></a><a name="getrect"></a>CToolBarCtrl::GetRect  
 检索指定的工具栏按钮的边框。  
  
```  
BOOL GetRect(
    int nID,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 按钮标识符。  
  
 `lpRect`  
 一个指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)接收边界的矩形信息的结构。  
  
### <a name="return-value"></a>返回值  
 **TRUE**成功，否则为如果**FALSE**。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb787346)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetrowsa--ctoolbarctrlgetrows"></a><a name="getrows"></a>CToolBarCtrl::GetRows  
 检索当前显示在工具栏控件的按钮的行数。  
  
```  
int GetRows() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前显示在工具栏上的按钮的行数。  
  
### <a name="remarks"></a>备注  
 请注意，行数将始终是一个除非使用创建工具栏`TBSTYLE_WRAPABLE`样式。  
  
##  <a name="a-namegetstatea--ctoolbarctrlgetstate"></a><a name="getstate"></a>CToolBarCtrl::GetState  
 检索有关指定的按钮在工具栏控件中，例如操作是已启用、 按下，还是已检查的状态信息。  
  
```  
int GetState(int nID) const;  
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 要检索其信息的按钮的命令标识符。  
  
### <a name="return-value"></a>返回值  
 如果成功的按钮状态信息或者-1 以其他方式。 按钮状态信息会中列出的值的组合[CToolBarCtrl::AddButtons](#addbuttons)。  
  
### <a name="remarks"></a>备注  
 此函数是如果您想要检索多个按钮状态尤为方便。 若要只检索一个状态，请使用以下成员函数之一︰ [IsButtonEnabled](#isbuttonenabled)， [IsButtonChecked](#isbuttonchecked)， [IsButtonPressed](#isbuttonpressed)， [IsButtonHidden](#isbuttonhidden)，或[IsButtonIndeterminate](#isbuttonindeterminate)。 但是，`GetState`成员函数是唯一的方法来检测`TBSTATE_WRAP`按钮状态。  
  
##  <a name="a-namegetstringa--ctoolbarctrlgetstring"></a><a name="getstring"></a>CToolBarCtrl::GetString  
 检索工具栏字符串。  
  
```  
int GetString(
    int nString,  
    LPTSTR lpstrString,  
    int cchMaxLen) const;  
  
int GetString(
    int nString,  
    CString& str) const;  
```  
  
### <a name="parameters"></a>参数  
 *nString*  
 字符串的索引。  
  
 *lpstrString*  
 指向用于返回的字符串的缓冲区的指针。  
  
 *cchMaxLen*  
 以字节为单位的缓冲区的长度。  
  
 `str`  
 字符串。  
  
### <a name="return-value"></a>返回值  
 如果成功，该字符串的长度时不为-1。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_GETSTRING](http://msdn.microsoft.com/library/windows/desktop/bb787349)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetstylea--ctoolbarctrlgetstyle"></a><a name="getstyle"></a>CToolBarCtrl::GetStyle  
 获取当前应用于工具栏控件的样式。  
  
```  
DWORD GetStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`DWORD`包含的一个组合[工具栏控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760439)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettooltipsa--ctoolbarctrlgettooltips"></a><a name="gettooltips"></a>CToolBarCtrl::GetToolTips  
 如果有的话关联工具栏控件中检索工具提示控件，句的柄。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)与此工具栏相关的对象或**NULL**如果该工具栏不具有任何关联的工具提示控件。  
  
### <a name="remarks"></a>备注  
 工具栏控件通常创建并维护其自己的工具提示控件，因为大多数程序无需调用此函数。  
  
##  <a name="a-namehittesta--ctoolbarctrlhittest"></a><a name="hittest"></a>CToolBarCtrl::HitTest  
 确定工具栏控件中的一个点所在。  
  
```  
int HitTest(LPPOINT ppt) const;  
```  
  
### <a name="parameters"></a>参数  
 `ppt`  
 一个指向[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)结构，它包含中的命中测试的 x 坐标**x**成员和 y 坐标的命中测试中**y**成员。 坐标是相对于工具栏的工作区。  
  
### <a name="return-value"></a>返回值  
 一个整数值，该值指示工具栏上的点的位置。 如果值为零或正数，则此返回值是点存在于 nonseparator 项的从零开始的索引。  
  
 如果返回值为负，则该点没有位于一个按钮。 返回值的绝对值是分隔符项或最近的 nonseparator 项的索引。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb787360)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namehidebuttona--ctoolbarctrlhidebutton"></a><a name="hidebutton"></a>CToolBarCtrl::HideButton  
 隐藏或显示指定的按钮在工具栏控件中。  
  
```  
BOOL HideButton(
    int nID,  
    BOOL bHide = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 若要隐藏或显示该按钮的命令标识符。  
  
 `bHide`  
 **TRUE**来隐藏按钮， **FALSE**来显示它。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 如果您想要更改多个按钮的状态，请考虑调用[SetState](#setstate)相反。  
  
##  <a name="a-nameindeterminatea--ctoolbarctrlindeterminate"></a><a name="indeterminate"></a>CToolBarCtrl::Indeterminate  
 设置或清除指定按钮在工具栏控件中的不确定状态。  
  
```  
BOOL Indeterminate(
    int nID,  
    BOOL bIndeterminate = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 不确定状态是要设置或清除按钮的命令标识符。  
  
 *bIndeterminate*  
 **TRUE**可设置指定按钮的不确定状态**FALSE**以将其清除。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 不确定显示按钮灰显，如字处理器的方式加粗按钮在工具栏上看当选定的文本包含显示为粗体和常规字符。 如果您想要更改多个按钮的状态，请考虑调用[SetState](#setstate)相反。  
  
##  <a name="a-nameinsertbuttona--ctoolbarctrlinsertbutton"></a><a name="insertbutton"></a>CToolBarCtrl::InsertButton  
 在工具栏控件中插入一个按钮。  
  
```  
BOOL InsertButton(
    int nIndex,  
    LPTBBUTTON lpButton);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 一个按钮的从零开始索引。 此函数将插入到此按钮左新建按钮。  
  
 `lpButton`  
 地址的指针`TBBUTTON`结构，它包含有关插入按钮的信息。 请参阅[CToolBarCtrl::AddButtons](#addbuttons)有关的说明`TBBUTTON`结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 使用图像和/或您提供其索引以前必须已添加到工具栏控件的字符串列出[AddBitmap](#addbitmap)， [AddString](#addstring)，和/或[AddStrings](#addstrings)。  
  
##  <a name="a-nameinsertmarkhittesta--ctoolbarctrlinsertmarkhittest"></a><a name="insertmarkhittest"></a>CToolBarCtrl::InsertMarkHitTest  
 检索在工具栏中的点的插入标记信息。  
  
```  
BOOL InsertMarkHitTest(
    LPPOINT ppt,  
    LPTBINSERTMARK ptbim) const;  
```  
  
### <a name="parameters"></a>参数  
 `ppt`  
 一个指向[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)结构，其中包含命中的测试协调，工具栏上的工作区相对。  
  
 `ptbim`  
 一个指向[TBINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb760480)接收插入标记信息的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_INSERTMARKHITTEST](http://msdn.microsoft.com/library/windows/desktop/bb787367)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameisbuttoncheckeda--ctoolbarctrlisbuttonchecked"></a><a name="isbuttonchecked"></a>CToolBarCtrl::IsButtonChecked  
 确定是否已选中指定按钮在工具栏控件中。  
  
```  
BOOL IsButtonChecked(int nID) const;  
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 在工具栏按钮的命令标识符。  
  
### <a name="return-value"></a>返回值  
 非零，如果已选中按钮;否则为零。  
  
### <a name="remarks"></a>备注  
 请考虑调用[GetState](#getstate)如果想要检索多个按钮的状态。  
  
##  <a name="a-nameisbuttonenableda--ctoolbarctrlisbuttonenabled"></a><a name="isbuttonenabled"></a>CToolBarCtrl::IsButtonEnabled  
 确定是否启用指定的按钮在工具栏控件中。  
  
```  
BOOL IsButtonEnabled(int nID) const;  
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 在工具栏按钮的命令标识符。  
  
### <a name="return-value"></a>返回值  
 如果启用按钮，则非零值否则为零。  
  
### <a name="remarks"></a>备注  
 请考虑调用[GetState](#getstate)如果想要检索多个按钮的状态。  
  
##  <a name="a-nameisbuttonhiddena--ctoolbarctrlisbuttonhidden"></a><a name="isbuttonhidden"></a>CToolBarCtrl::IsButtonHidden  
 确定指定的按钮在工具栏控件中是否处于隐藏状态。  
  
```  
BOOL IsButtonHidden(int nID) const;  
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 在工具栏按钮的命令标识符。  
  
### <a name="return-value"></a>返回值  
 按钮处于隐藏状态; 如果非零值否则为零。  
  
### <a name="remarks"></a>备注  
 请考虑调用[GetState](#getstate)如果想要检索多个按钮的状态。  
  
##  <a name="a-nameisbuttonhighlighteda--ctoolbarctrlisbuttonhighlighted"></a><a name="isbuttonhighlighted"></a>CToolBarCtrl::IsButtonHighlighted  
 检查工具栏按钮的突出显示状态。  
  
```  
BOOL IsButtonHighlighted(int nID) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 工具栏按钮的命令 ID。  
  
### <a name="return-value"></a>返回值  
 如果突出显示该按钮的正整数，如果未突出显示按钮，则为 0 或-1 如果检测到错误时发生。  
  
##  <a name="a-nameisbuttonindeterminatea--ctoolbarctrlisbuttonindeterminate"></a><a name="isbuttonindeterminate"></a>CToolBarCtrl::IsButtonIndeterminate  
 确定指定的按钮在工具栏控件中是不确定的。  
  
```  
BOOL IsButtonIndeterminate(int nID) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 在工具栏按钮的命令标识符。  
  
### <a name="return-value"></a>返回值  
 正整数如果按钮是不确定的如果零按钮不是不确定的或为-1 如果检测到错误发生。  
  
### <a name="remarks"></a>备注  
 不确定显示按钮变灰，如字处理器的方式在工具栏上加粗按钮时所选的文本中包含显示为粗体和常规字符的外观。 请考虑调用[GetState](#getstate)如果想要检索多个按钮的状态。  
  
##  <a name="a-nameisbuttonpresseda--ctoolbarctrlisbuttonpressed"></a><a name="isbuttonpressed"></a>CToolBarCtrl::IsButtonPressed  
 确定是否按下工具栏控件中指定的按钮。  
  
```  
BOOL IsButtonPressed(int nID) const;  
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 在工具栏按钮的命令标识符。  
  
### <a name="return-value"></a>返回值  
 如果该按钮后，否则为零，非零值。  
  
### <a name="remarks"></a>备注  
 请考虑调用[GetState](#getstate)如果想要检索多个按钮的状态。  
  
##  <a name="a-nameloadimagesa--ctoolbarctrlloadimages"></a><a name="loadimages"></a>CToolBarCtrl::LoadImages  
 将位图加载到工具栏控件的图像列表。  
  
```  
void LoadImages(
    int iBitmapID,  
    HINSTANCE hinst);
```  
  
### <a name="parameters"></a>参数  
 *iBitmapID*  
 包含要加载的图像的位图的 ID。 若要指定您自己的位图资源，请将此参数设置为位图资源的 ID，并设置`hInst`到**NULL**。 位图资源将添加到映像列表中，作为单个图像。 您可以通过设置添加标准的系统定义位图*hinst*到**HINST_COMMCTRL**并将此参数设置为下列 Id 之一︰  
  
|位图的 ID|描述|  
|---------------|-----------------|  
|IDB_HIST_LARGE_COLOR|资源管理器中较大的大小的位图|  
|IDB_HIST_SMALL_COLOR|资源管理器位图以小的尺寸|  
|IDB_STD_LARGE_COLOR|大的标准位图|  
|IDB_STD_SMALL_COLOR|标准位图以小的尺寸|  
|IDB_VIEW_LARGE_COLOR|在大尺寸的视图位图|  
|IDB_VIEW_SMALL_COLOR|视图位图以小的尺寸|  
  
 *hinst*  
 调用应用程序实例句柄。 此参数可以为**HINST_COMMCTRL**加载一个标准的图像列表。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_LOADIMAGES](http://msdn.microsoft.com/library/windows/desktop/bb787381)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namemapacceleratora--ctoolbarctrlmapaccelerator"></a><a name="mapaccelerator"></a>CToolBarCtrl::MapAccelerator  
 将一个加速器字符映射到一个工具栏按钮。  
  
```  
BOOL MapAccelerator(
    TCHAR chAccel,  
    UINT* pIDBtn);
```  
  
### <a name="parameters"></a>参数  
 `chAccel`  
 要映射的加速器字符。 该字符为同一个按钮的文本中带下划线的字符。  
  
 *pIDBtn*  
 一个指向**UINT** ，它接收到加速器中指定对应的按钮的命令标识符`chAccel`。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_MAPACCELERATOR](http://msdn.microsoft.com/library/windows/desktop/bb787383)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namemarkbuttona--ctoolbarctrlmarkbutton"></a><a name="markbutton"></a>CToolBarCtrl::MarkButton  
 在工具栏控件中设置给定的按钮的突出显示状态。  
  
```  
BOOL MarkButton(
    int nID,  
    BOOL fHighlight = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 按钮标识符。  
  
 `fHighlight`  
 指定要设置的突出显示状态。 默认情况下， **TRUE**。 如果设置为**FALSE**，按钮设置为其默认状态。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_MARKBUTTON](http://msdn.microsoft.com/library/windows/desktop/bb787385)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namemovebuttona--ctoolbarctrlmovebutton"></a><a name="movebutton"></a>CToolBarCtrl::MoveButton  
 将一个按钮从一个索引移到另一个。  
  
```  
BOOL MoveButton(
    UINT nOldPos,  
    UINT nNewPos);
```  
  
### <a name="parameters"></a>参数  
 *nOldPos*  
 移动按钮从零开始索引。  
  
 *nNewPos*  
 该按钮的目标的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_MOVEBUTTON](http://msdn.microsoft.com/library/windows/desktop/bb787387)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namepressbuttona--ctoolbarctrlpressbutton"></a><a name="pressbutton"></a>CToolBarCtrl::PressButton  
 按下或释放在工具栏控件中指定的按钮。  
  
```  
BOOL PressButton(int nID, BOOL bPress = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 若要按下或释放该按钮的命令标识符。  
  
 [in] `bPress`  
 `true`若要按指定的按钮;`false`释放指定的按钮。 默认值为 `true`。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 如果您想要更改多个按钮的状态，请考虑调用[SetState](#setstate)相反。  
  
 此方法可发送[TB_PRESSBUTTON](http://msdn.microsoft.com/library/windows/desktop/bb787389)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namereplacebitmapa--ctoolbarctrlreplacebitmap"></a><a name="replacebitmap"></a>CToolBarCtrl::ReplaceBitmap  
 用新位图替换当前的工具栏控件中现有的位图。  
  
```  
BOOL ReplaceBitmap(LPTBREPLACEBITMAP pReplaceBitmap);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pReplaceBitmap`|指向[TBREPLACEBITMAP](http://msdn.microsoft.com/library/windows/desktop/bb760484)结构描述要被替换的位图和新的位图。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TB_REPLACEBITMAP](http://msdn.microsoft.com/library/windows/desktop/bb787391)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例将标准工具栏的位图替换不同的位图。  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s&#1;&2;](../../mfc/reference/codesnippet/cpp/ctoolbarctrl-class_4.cpp)]  
  
##  <a name="a-namerestorestatea--ctoolbarctrlrestorestate"></a><a name="restorestate"></a>CToolBarCtrl::RestoreState  
 从参数所指定的注册表中的位置还原工具栏控件的状态。  
  
```  
void RestoreState(
    HKEY hKeyRoot,  
    LPCTSTR lpszSubKey,  
    LPCTSTR lpszValueName);
```  
  
### <a name="parameters"></a>参数  
 `hKeyRoot`  
 标识一个当前打开的项在注册表或任何以下预定义保留的句柄值︰  
  
- **HKEY_CLASSES_ROOT**  
  
- **HKEY_CURRENT_USER**  
  
- **HKEY_LOCAL_MACHINE**  
  
- **HKEY_USERS**  
  
 `lpszSubKey`  
 指向以 null 结尾的字符串包含一个值与之关联的子项的名称。 此参数可以为 null 或为空字符串的指针。 如果参数是**NULL**，值将添加到由标识键`hKeyRoot`参数。  
  
 `lpszValueName`  
 指向包含要检索的值的名称的字符串。 如果具有此名称的值尚不存在项中，该函数会将其添加到该密钥。  
  
##  <a name="a-namesavestatea--ctoolbarctrlsavestate"></a><a name="savestate"></a>CToolBarCtrl::SaveState  
 将工具栏控件的状态保存在由参数指定的注册表中的位置。  
  
```  
void SaveState(
    HKEY hKeyRoot,  
    LPCTSTR lpszSubKey,  
    LPCTSTR lpszValueName);
```  
  
### <a name="parameters"></a>参数  
 `hKeyRoot`  
 标识一个当前打开的项在注册表或任何以下预定义保留的句柄值︰  
  
- **HKEY_CLASSES_ROOT**  
  
- **HKEY_CURRENT_USER**  
  
- **HKEY_LOCAL_MACHINE**  
  
- **HKEY_USERS**  
  
 `lpszSubKey`  
 指向以 null 结尾的字符串包含一个值与之关联的子项的名称。 此参数可以为 null 或为空字符串的指针。 如果参数是**NULL**，值将添加到由标识键`hKeyRoot`参数。  
  
 `lpszValueName`  
 指向包含要设置的值的名称的字符串。 如果具有此名称的值尚不存在项中，该函数会将其添加到该密钥。  
  
##  <a name="a-namesetanchorhighlighta--ctoolbarctrlsetanchorhighlight"></a><a name="setanchorhighlight"></a>CToolBarCtrl::SetAnchorHighlight  
 设置设置为工具栏的定位点突出显示。  
  
```  
BOOL SetAnchorHighlight(BOOL fAnchor = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `fAnchor`  
 指定是启用还是禁用定位点突出显示。 如果此值不为零，则将启用定位点突出显示。 如果此值为零，将禁用定位点突出显示  
  
### <a name="return-value"></a>返回值  
 以前的定位点设置。 如果启用了突出显示，此值不为零。 如果未启用突出显示，则此值为零。  
  
### <a name="remarks"></a>备注  
 此方法实现的行为的 Win32 消息[TB_SETANCHORHIGHLIGHT](http://msdn.microsoft.com/library/windows/desktop/bb787396)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetbitmapsizea--ctoolbarctrlsetbitmapsize"></a><a name="setbitmapsize"></a>CToolBarCtrl::SetBitmapSize  
 设置实际位图化图像添加到工具栏控件的大小。  
  
```  
BOOL SetBitmapSize(CSize size);
```  
  
### <a name="parameters"></a>参数  
 `size`  
 宽度和高度，以像素为单位的位图图像。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 仅在添加到工具栏上的任何位图之前必须调用此函数。 如果应用程序未显式设置位图的大小，则默认为 16 x 15 像素。  
  
##  <a name="a-namesetbuttoninfoa--ctoolbarctrlsetbuttoninfo"></a><a name="setbuttoninfo"></a>CToolBarCtrl::SetButtonInfo  
 在工具栏中设置的现有按钮的信息。  
  
```  
BOOL SetButtonInfo(
    int nID,  
    TBBUTTONINFO* ptbbi);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 按钮标识符。  
  
 `ptbbi`  
 一个指向[TBBUTTONINFO](http://msdn.microsoft.com/library/windows/desktop/bb760478)接收按钮信息的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 成员函数实现的行为的 Win32 消息[TB_SETBUTTONINFO](http://msdn.microsoft.com/library/windows/desktop/bb787413)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetbuttonsizea--ctoolbarctrlsetbuttonsize"></a><a name="setbuttonsize"></a>CToolBarCtrl::SetButtonSize  
 在工具栏控件中设置按钮的大小。  
  
```  
BOOL SetButtonSize(CSize size);
```  
  
### <a name="parameters"></a>参数  
 `size`  
 宽度和高度，以像素为单位的按钮。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 该按钮的大小必须始终至少与它包含位图的大小一样大。 仅在添加到工具栏上的任何位图之前必须调用此函数。 如果应用程序未显式设置该按钮的大小，则默认为 24 x 22 像素。  
  
### <a name="example"></a>示例  
  请参阅示例[CToolBar::GetToolBarCtrl](../../mfc/reference/ctoolbar-class.md#gettoolbarctrl)。  
  
##  <a name="a-namesetbuttonstructsizea--ctoolbarctrlsetbuttonstructsize"></a><a name="setbuttonstructsize"></a>CToolBarCtrl::SetButtonStructSize  
 指定的大小`TBBUTTON`结构。  
  
```  
void SetButtonStructSize(int nSize);
```  
  
### <a name="parameters"></a>参数  
 `nSize`  
 设置大小，以字节为单位的`TBBUTTON`结构。  
  
### <a name="remarks"></a>备注  
 如果你想要存储中的额外数据`TBBUTTON`结构，可能既派生新结构从`TBBUTTON`，添加成员需要也可以创建新的结构，其中包含`TBBUTTON`结构作为其第一个成员。 随后，您就可以调用此函数以告知工具栏控件的新结构的大小。  
  
 请参阅[CToolBarCtrl::AddButtons](#addbuttons)有关详细信息`TBBUTTON`结构。  
  
##  <a name="a-namesetbuttonwidtha--ctoolbarctrlsetbuttonwidth"></a><a name="setbuttonwidth"></a>CToolBarCtrl::SetButtonWidth  
 在工具栏控件中设置的最小值和最大按钮的宽度。  
  
```  
BOOL SetButtonWidth(
    int cxMin,  
    int cxMax);
```  
  
### <a name="parameters"></a>参数  
 `cxMin`  
 最小按钮宽度，以像素为单位。 工具栏按钮将永远不能超过此值更窄。  
  
 *cxMax*  
 最大按钮的宽度，以像素为单位。 如果按钮文本是太宽，该控件将显示其与省略号点。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_SETBUTTONWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb787417)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetcmdida--ctoolbarctrlsetcmdid"></a><a name="setcmdid"></a>CToolBarCtrl::SetCmdID  
 设置指定的按钮按下时，将向所有者窗口发送的命令标识符。  
  
```  
BOOL SetCmdID(
    int nIndex,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 其命令 ID 是将按钮的从零开始索引。  
  
 `nID`  
 要设置为所选的按钮的命令 ID。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零返回否则为零。  
  
##  <a name="a-namesetcolorschemea--ctoolbarctrlsetcolorscheme"></a><a name="setcolorscheme"></a>CToolBarCtrl::SetColorScheme  
 设置当前的工具栏控件的配色方案。  
  
```  
void SetColorScheme(const COLORSCHEME* lpColorScheme);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `lpColorScheme`|指向[要添加的配色](http://msdn.microsoft.com/library/windows/desktop/bb775502)描述突出显示颜色和阴影颜色工具栏控件的结构。|  
  
### <a name="remarks"></a>备注  
 此方法不起作用如果[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]visual 主题设置。  
  
 此方法可发送[TB_SETCOLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb787421)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例设置当前的工具栏控件的配色方案。 代码示例将每个工具按钮红色的 left 和 top 边缘和右边缘和下边缘蓝色。 当用户按下按钮时，该按钮的红色边缘打开蓝色，其蓝色边缘变为红色。  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s&#1;&3;](../../mfc/reference/codesnippet/cpp/ctoolbarctrl-class_5.cpp)]  
  
##  <a name="a-namesetdisabledimagelista--ctoolbarctrlsetdisabledimagelist"></a><a name="setdisabledimagelist"></a>CToolBarCtrl::SetDisabledImageList  
 将工具栏控件将使用的图像列表设置为显示禁用按钮。  
  
```  
CImageList* SetDisabledImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>参数  
 `pImageList`  
 一个指向`CImageList`对象，其中包含要使用工具栏控件到显示禁用按钮图像的图像。  
  
### <a name="return-value"></a>返回值  
 一个指向[CImageList](../../mfc/reference/cimagelist-class.md)以前使用的到显示禁用按钮图像的工具栏控件的对象。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_SETDISABLEDIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787423)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 MFC 实现`SetDisabledImageList`使用`CImageList`对象，包含工具栏控件的禁用的按钮映像，而不是图像列表的句柄。  
  
##  <a name="a-namesetdrawtextflagsa--ctoolbarctrlsetdrawtextflags"></a><a name="setdrawtextflags"></a>CToolBarCtrl::SetDrawTextFlags  
 Win32 函数中设置的标志[DrawText](http://msdn.microsoft.com/library/windows/desktop/dd162498)，用于按照如何设置的标志设置格式的指定矩形中绘制文本。  
  
```  
DWORD SetDrawTextFlags(
    DWORD dwMask,  
    DWORD dwDTFlags);
```  
  
### <a name="parameters"></a>参数  
 `dwMask`  
 一个或多个 Win32 函数中指定的 DT_ 标志的组合[DrawText](http://msdn.microsoft.com/library/windows/desktop/dd162498)，指示该位在`dwDTFlags`绘制文本时，将使用。  
  
 `dwDTFlags`  
 一个或多个 Win32 函数中指定的 DT_ 标志的组合`DrawText`，指示将如何绘制按钮文本。 此值传递给`DrawText`何时绘制按钮文本。  
  
### <a name="return-value"></a>返回值  
 一个`DWORD`包含以前的文本绘制标志。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_SETDRAWTEXTFLAGS](http://msdn.microsoft.com/library/windows/desktop/bb787425)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 此成员函数的 Win32 函数中设置的标志`DrawText`，按照如何设置的标志设置格式的指定矩形中绘制文本的。  
  
##  <a name="a-namesetextendedstylea--ctoolbarctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CToolBarCtrl::SetExtendedStyle  
 设置工具栏控件的扩展的样式。  
  
```  
DWORD SetExtendedStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwExStyle`  
 指定新的扩展的样式的值。 此参数可以为扩展样式工具栏上的组合。  
  
### <a name="return-value"></a>返回值  
 一个`DWORD`的上一个表示扩展样式。 有关样式的列表，请参阅[工具栏扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb760430)，请在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb787427)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesethotimagelista--ctoolbarctrlsethotimagelist"></a><a name="sethotimagelist"></a>CToolBarCtrl::SetHotImageList  
 设置工具栏控件将用于显示"热"按钮的图像列表。  
  
```  
CImageList* SetHotImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>参数  
 `pImageList`  
 一个指向`CImageList`对象，其中包含由工具栏控件用于显示热按钮图像的图像。  
  
### <a name="return-value"></a>返回值  
 一个指向[CImageList](../../mfc/reference/cimagelist-class.md)以前使用的工具栏控件用于显示热按钮图像的对象。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_SETHOTIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787429)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 MFC 实现`SetHotImageList`使用`CImageList`对象，包含工具栏控件的热点问题映像，而不是图像列表的句柄。 当指针位于其上方时突出显示热按钮。  
  
##  <a name="a-namesethotitema--ctoolbarctrlsethotitem"></a><a name="sethotitem"></a>CToolBarCtrl::SetHotItem  
 在工具栏中设置的热的项。  
  
```  
int SetHotItem(int nHot);
```  
  
### <a name="parameters"></a>参数  
 *nHot*  
 将成为热的项的从零开始的索引号。 如果此值为-1，没有任何项将热。  
  
### <a name="return-value"></a>返回值  
 前一热项，则为-1 如果没有任何热项的索引。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_SETHOTITEM](http://msdn.microsoft.com/library/windows/desktop/bb787431)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetimagelista--ctoolbarctrlsetimagelist"></a><a name="setimagelist"></a>CToolBarCtrl::SetImageList  
 设置工具栏上将用来显示它们的默认状态的按钮的图像列表。  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>参数  
 `pImageList`  
 一个指向`CImageList`对象，其中包含要用于通过工具栏控件及其默认状态中显示按钮图像的图像。  
  
### <a name="return-value"></a>返回值  
 一个指向[CImageList](../../mfc/reference/cimagelist-class.md)以前使用的工具栏控件来显示按钮图像在其默认状态的对象。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_SETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787433)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 MFC 实现`SetImageList`使用`CImageList`对象，包含工具栏控件的按钮映像，而不是图像列表的句柄。  
  
##  <a name="a-namesetindenta--ctoolbarctrlsetindent"></a><a name="setindent"></a>CToolBarCtrl::SetIndent  
 设置工具栏控件中的第一个按钮的缩进。  
  
```  
BOOL SetIndent(int iIndent);
```  
  
### <a name="parameters"></a>参数  
 *iIndent*  
 指定缩进，以像素为单位的值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
##  <a name="a-namesetinsertmarka--ctoolbarctrlsetinsertmark"></a><a name="setinsertmark"></a>CToolBarCtrl::SetInsertMark  
 设置工具栏上的当前插入标记。  
  
```  
void SetInsertMark(TBINSERTMARK* ptbim);
```  
  
### <a name="parameters"></a>参数  
 `ptbim`  
 一个指向[TBINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb760480)结构，其中包含插入标记。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_SETINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb787437)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetinsertmarkcolora--ctoolbarctrlsetinsertmarkcolor"></a><a name="setinsertmarkcolor"></a>CToolBarCtrl::SetInsertMarkColor  
 设置用于绘制工具栏上的插入标记的颜色。  
  
```  
COLORREF SetInsertMarkColor(COLORREF clrNew);
```  
  
### <a name="parameters"></a>参数  
 `clrNew`  
 一个**COLORREF**值，该值包含新的插入标记颜色。  
  
### <a name="return-value"></a>返回值  
 一个**COLORREF**值，该值包含以前的插入标记颜色。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TB_SETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb787439)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetmaxtextrowsa--ctoolbarctrlsetmaxtextrows"></a><a name="setmaxtextrows"></a>CToolBarCtrl::SetMaxTextRows  
 设置最大工具栏按钮上显示的文本行数。  
  
```  
BOOL SetMaxTextRows(int iMaxRows);
```  
  
### <a name="parameters"></a>参数  
 *iMaxRows*  
 要设置的行的最大数量。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
##  <a name="a-namesetmetricsa--ctoolbarctrlsetmetrics"></a><a name="setmetrics"></a>CToolBarCtrl::SetMetrics  
 设置的度量值`CToolBarCtrl`对象。  
  
```  
void SetMetrics(LPTBMETRICS ptbm);
```  
  
### <a name="parameters"></a>参数  
 `ptbm`  
 一个指向[TBMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb760482)结构`CToolBarCtrl`对象。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[TB_SETMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb787446)消息，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetownera--ctoolbarctrlsetowner"></a><a name="setowner"></a>CToolBarCtrl::SetOwner  
 设置工具栏控件的所有者窗口。  
  
```  
void SetOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向`CWnd`或`CWnd`-派生该对象将作为工具栏控件的新的所有者窗口。  
  
### <a name="remarks"></a>备注  
 所有者窗口是接收通知，从工具栏中的窗口。  
  
##  <a name="a-namesetpaddinga--ctoolbarctrlsetpadding"></a><a name="setpadding"></a>CToolBarCtrl::SetPadding  
 设置当前的工具栏控件的水平和垂直填充。  
  
```  
DWORD SetPadding(
    int nHorzPadding,   
    int nVertPadding);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `nHorzPadding`|以像素为单位指定工具栏控件的水平边距。|  
|[in] `nVertPadding`|以像素为单位指定工具栏控件的垂直边距。|  
  
### <a name="return-value"></a>返回值  
 一个`DWORD`其低位字包含以前的水平空白值，而其高位字包含以前的垂直空白值。 以像素为单位度量的空白值。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TB_SETPADDING](http://msdn.microsoft.com/library/windows/desktop/bb787448)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例将当前的工具栏控件的水平和垂直边距设置为 20 个像素。  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s&#1;&4;](../../mfc/reference/codesnippet/cpp/ctoolbarctrl-class_6.cpp)]  
  
##  <a name="a-namesetpressedimagelista--ctoolbarctrlsetpressedimagelist"></a><a name="setpressedimagelist"></a>CToolBarCtrl::SetPressedImageList  
 设置当前的工具栏控件使用以表示按钮处于按下状态的图像列表。  
  
```  
CImagelist* SetPressedImageList(
    int iImageID,   
    CImageList* pImageList);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `iImageID`|图像列表的从零开始的索引。 如果你只有一个图像列表中使用此参数设置为零。|  
|[in] `pImageList`|指向[CImageList](../../mfc/reference/cimagelist-class.md) ，其中包含新图像列表。|  
  
### <a name="return-value"></a>返回值  
 指向[CImageList](../../mfc/reference/cimagelist-class.md) ，其中包含当前控件的上一个图像列表或`NULL`如果任何此类图像列表不设置。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TB_SETPRESSEDIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787453)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例设置要与默认图像列表相同的按下的图像列表。  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s&#1;&5;](../../mfc/reference/codesnippet/cpp/ctoolbarctrl-class_7.cpp)]  
  
##  <a name="a-namesetrowsa--ctoolbarctrlsetrows"></a><a name="setrows"></a>CToolBarCtrl::SetRows  
 将询问工具栏控件来调整其自身到请求的行数大小。  
  
```  
void SetRows(
    int nRows,  
    BOOL bLarger,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `nRows`  
 请求的行数。  
  
 `bLarger`  
 指示是否使用更多的行或更少的行，如果不能将工具栏大小调整到请求的行数。  
  
 `lpRect`  
 指向[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它将收到工具栏上的新边框。  
  
### <a name="remarks"></a>备注  
 如果工具栏不能调整自身大小为请求的数或行中，它将调整自身大小为下一步变大或下一个较小有效大小，具体取决于值`bLarger`。 如果`bLarger`是**TRUE**，新的行数将大于请求的数目。 如果`bLarger`是**FALSE**，新的行数将小于请求的数目。  
  
 当这些按钮可以排列的所有行具有相同数量的 （除了可能的最后一行） 按钮，指定的数目的行才有效的工具栏。 例如，包含四个按钮的工具栏可以不进行大小调整为三行因为最后两行必须越短。 如果您尝试调整其大小为三个行，则会得到四行，如果`bLarger`已**TRUE**和两个行如果`bLarger`已**FALSE**。  
  
 如果工具栏中分隔符，则指定的数目的行时有效的规则会更加复杂。 这样，按钮组 （使用分隔符之前第一个按钮） 并可以在组中的最后一个按钮要永远不会断开，在多个行上除非组无法容纳一行，计算布局。  
  
 如果一组不适合在一行上下, 一组将启动到下一行，即使它将容纳在行大组结束的地方。 该规则的目的是使更明显的大型组之间的分离。 生成的垂直分隔符计为行。  
  
 另请注意，`SetRows`成员函数将始终选择最小工具栏大小会导致的布局。 创建一个带有工具栏`TBSTYLE_WRAPABLE`样式，然后调整控件的大小将只需将应用上述给定控件的宽度的方法。  
  
 此函数只能调用使用以前创建的工具栏`TBSTYLE_WRAPABLE`样式。  
  
##  <a name="a-namesetstatea--ctoolbarctrlsetstate"></a><a name="setstate"></a>CToolBarCtrl::SetState  
 在工具栏控件中设置指定按钮的状态。  
  
```  
BOOL SetState(
    int nID,  
    UINT nState);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 该按钮的命令标识符。  
  
 `nState`  
 状态标志。 它可以是对按钮状态列出的值的组合[CToolBarCtrl::AddButtons](#addbuttons)。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 此函数是如果您想要设置多个按钮状态尤为方便。 若要只需设置一种状态，使用以下成员函数之一︰ [EnableButton](#enablebutton)， [CheckButton](#checkbutton)， [HideButton](#hidebutton)，[不确定](#indeterminate)，或[PressButton](#pressbutton)。  
  
##  <a name="a-namesetstylea--ctoolbarctrlsetstyle"></a><a name="setstyle"></a>CToolBarCtrl::SetStyle  
 设置工具栏控件的样式。  
  
```  
void SetStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 一个`DWORD`包含的一个组合[工具栏控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760439)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesettooltipsa--ctoolbarctrlsettooltips"></a><a name="settooltips"></a>CToolBarCtrl::SetToolTips  
 将工具提示控件与工具栏控件相关联。  
  
```  
void SetToolTips(CToolTipCtrl* pTip);
```  
  
### <a name="parameters"></a>参数  
 *pTip*  
 指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象。  
  
##  <a name="a-namesetwindowthemea--ctoolbarctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CToolBarCtrl::SetWindowTheme  
 设置的视觉样式`CToolBarCtrl`对象。  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>参数  
 `pszSubAppName`  
 指向包含要设置的工具栏视觉样式的 Unicode 字符串的指针。  
  
### <a name="return-value"></a>返回值  
 不使用返回的值。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[TB_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb787465)消息，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CMNCTRL1](../../visual-cpp-samples.md)   
 [MFC 示例 MFCIE](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CToolBar 类](../../mfc/reference/ctoolbar-class.md)

