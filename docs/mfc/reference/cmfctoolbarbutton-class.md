---
title: "CMFCToolBarButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarButton class
ms.assetid: 8a6ecffb-86b0-4f5c-8211-a9146b463efd
caps.latest.revision: 34
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
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 0139779cd00a514684c20b2c589d96247a532733
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarbutton-class"></a>CMFCToolBarButton 类
提供为工具栏按钮功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCToolBarButton : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarButton::CMFCToolBarButton](#cmfctoolbarbutton)|构造并初始化一个 `CMFCToolBarButton` 对象。|  
|`CMFCToolBarButton::~CMFCToolBarButton`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarButton::CanBeDropped](#canbedropped)|指定用户是否可以定位自定义期间的工具栏或菜单上的按钮。|  
|[CMFCToolBarButton::CanBeStored](#canbestored)|指定是否可以存储按钮。|  
|[CMFCToolBarButton::CanBeStretched](#canbestretched)|指定用户是否可以自定义期间拉伸按钮。|  
|[CMFCToolBarButton::CompareWith](#comparewith)|将此实例与提供`CMFCToolBarButton`对象。|  
|[CMFCToolBarButton::CopyFrom](#copyfrom)|将另一个工具栏按钮的属性复制到当前按钮。|  
|[CMFCToolBarButton::CreateFromOleData](#createfromoledata)|创建`CMFCToolBarButton`从所提供的对象`COleDataObject`对象。|  
|`CMFCToolBarButton::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCToolBarButton::EnableWindow](#enablewindow)|启用或禁用鼠标和键盘输入。|  
|[CMFCToolBarButton::ExportToMenuButton](#exporttomenubutton)|复制从工具栏按钮的文本复制到菜单。|  
|[CMFCToolBarButton::GetClipboardFormat](#getclipboardformat)|检索应用程序的全局剪贴板格式。|  
|[CMFCToolBarButton::GetHwnd](#gethwnd)|检索与工具栏按钮关联的窗口句柄。|  
|[CMFCToolBarButton::GetImage](#getimage)|检索按钮的图像索引。|  
|[CMFCToolBarButton::GetInvalidateRect](#getinvalidaterect)|检索的工作区的按钮必须重绘的区域。|  
|[CMFCToolBarButton::GetParentWnd](#getparentwnd)|检索父窗口的按钮。|  
|[CMFCToolBarButton::GetProtectedCommands](#getprotectedcommands)|检索用户不能自定义的命令的列表。|  
|[CMFCToolBarButton::GetTextSize](#gettextsize)|检索按钮文本的大小。|  
|[CMFCToolBarButton::HasFocus](#hasfocus)|确定该按钮是否具有当前输入的焦点。|  
|[CMFCToolBarButton::HaveHotBorder](#havehotborder)|确定当用户选择该按钮是否显示按钮的边框。|  
|[CMFCToolBarButton::IsDrawImage](#isdrawimage)|确定是否在按钮上显示图像。|  
|[CMFCToolBarButton::IsDrawText](#isdrawtext)|确定是否在按钮上显示的文本标签。|  
|[CMFCToolBarButton::IsDroppedDown](#isdroppeddown)|确定按钮是否显示子菜单。|  
|[CMFCToolBarButton::IsEditable](#iseditable)|确定是否可以自定义按钮。|  
|[CMFCToolBarButton::IsExtraSize](#isextrasize)|确定是否可以使用扩展的边框来显示按钮。|  
|[CMFCToolBarButton::IsFirstInGroup](#isfirstingroup)|确定是否在其按钮组中的第一个位置为按钮。|  
|[CMFCToolBarButton::IsHidden](#ishidden)|确定按钮处于隐藏状态。|  
|[CMFCToolBarButton::IsHorizontal](#ishorizontal)|确定是否将该按钮处水平工具栏上。|  
|[CMFCToolBarButton::IsLastInGroup](#islastingroup)|指定的按钮是否在其按钮组中的最后一个位置中。|  
|[CMFCToolBarButton::IsLocked](#islocked)|确定是否已启用锁定的 （非可自定义） 工具栏上的按钮。|  
|[CMFCToolBarButton::IsOwnerOf](#isownerof)|确定按钮是否提供的窗口句柄的所有者。|  
|[CMFCToolBarButton::IsVisible](#isvisible)|确定工具栏按钮是否可见。|  
|[CMFCToolBarButton::IsWindowVisible](#iswindowvisible)|确定基础窗口句柄的按钮是否可见。|  
|[CMFCToolBarButton::NotifyCommand](#notifycommand)|指定是否处理按钮[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)消息。|  
|[CMFCToolBarButton::OnAddToCustomizePage](#onaddtocustomizepage)|当该按钮添加到由框架调用**自定义**对话框。|  
|[CMFCToolBarButton::OnBeforeDrag](#onbeforedrag)|指定是否可拖动按钮。|  
|[CMFCToolBarButton::OnBeforeDrop](#onbeforedrop)|指定用户是否可以放到目标工具栏按钮。|  
|[CMFCToolBarButton::OnCalculateSize](#oncalculatesize)|调用由框架来计算指定的设备上下文和插接状态的按钮的大小。|  
|[CMFCToolBarButton::OnCancelMode](#oncancelmode)|由框架调用以处理[WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615)消息。|  
|[CMFCToolBarButton::OnChangeParentWnd](#onchangeparentwnd)|在按钮插入到一个新的工具栏时由框架调用。|  
|[CMFCToolBarButton::OnClick](#onclick)|在用户单击鼠标按钮时由框架调用。|  
|[CMFCToolBarButton::OnClickUp](#onclickup)|当用户释放鼠标按钮时由框架调用。|  
|[CMFCToolBarButton::OnContextHelp](#oncontexthelp)|当在父级工具栏处理由框架调用`WM_HELPHITTEST`消息。|  
|[CMFCToolBarButton::OnCtlColor](#onctlcolor)|当在父级工具栏处理由框架调用`WM_CTLCOLOR`消息。|  
|[CMFCToolBarButton::OnCustomizeMenu](#oncustomizemenu)|允许时应用程序显示在父级工具栏上的快捷菜单上，修改提供菜单按钮。|  
|[CMFCToolBarButton::OnDblClk](#ondblclk)|当在父级工具栏处理由框架调用[需知道 WM_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606)消息。|  
|[CMFCToolBarButton::OnDraw](#ondraw)|由框架通过使用指定的样式和选项绘制按钮调用。|  
|[CMFCToolBarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|由框架调用以将按钮画入**命令**窗格**自定义**对话框。|  
|[CMFCToolBarButton::OnGetCustomToolTipText](#ongetcustomtooltiptext)|由要检索按钮的自定义工具提示文本的框架调用。|  
|[CMFCToolBarButton::OnGlobalFontsChanged](#onglobalfontschanged)|当全局字体发生更改时由框架调用。|  
|[CMFCToolBarButton::OnMove](#onmove)|当在父级工具栏将由框架调用。|  
|[CMFCToolBarButton::OnShow](#onshow)|由框架调用时该按钮即变为可见或不可见。|  
|[CMFCToolBarButton::OnSize](#onsize)|在父级工具栏更改图形的大小或位置和此更改需要按钮以更改大小时由框架调用。|  
|[CMFCToolBarButton::OnToolHitTest](#ontoolhittest)|当在父级工具栏必须确定在点是否被按钮的边框时由框架调用。|  
|[CMFCToolBarButton::OnUpdateToolTip](#onupdatetooltip)|当在父级工具栏更新其工具提示文本由框架调用。|  
|[CMFCToolBarButton::PrepareDrag](#preparedrag)|要执行拖放操作按钮时由框架调用。|  
|[CMFCToolBarButton::Rect](#rect)|检索按钮的边框。|  
|[CMFCToolBarButton::ResetImageToDefault](#resetimagetodefault)|将设置为默认值是与按钮关联的图像。|  
|[CMFCToolBarButton::SaveBarState](#savebarstate)|保存工具栏按钮的状态。|  
|[CMFCToolBarButton::Serialize](#serialize)|从存档读取此对象或将其写入存档。 (重写[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)。)|  
|[CMFCToolBarButton::SetACCData](#setaccdata)|填充所提供`CAccessibilityData`对象从工具栏按钮可访问性数据。|  
|[CMFCToolBarButton::SetClipboardFormatName](#setclipboardformatname)|重命名的全局剪贴板格式。|  
|[CMFCToolBarButton::SetImage](#setimage)|设置按钮的图像索引。|  
|[CMFCToolBarButton::SetProtectedCommands](#setprotectedcommands)|设置用户不能自定义的命令的列表。|  
|[CMFCToolBarButton::SetRadio](#setradio)|当一个按钮将其选中的状态更改时由框架调用。|  
|[CMFCToolBarButton::SetRect](#setrect)|设置按钮的边框。|  
|[CMFCToolBarButton::SetStyle](#setstyle)|设置按钮样式。|  
|[CMFCToolBarButton::SetVisible](#setvisible)|指定的按钮是否可见。|  
|[CMFCToolBarButton::Show](#show)|显示或隐藏按钮。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarButton::m_bImage](#m_bimage)|指定是否在按钮上显示图像。|  
|[CMFCToolBarButton::m_bText](#m_btext)|指定是否在按钮上显示的文本标签。|  
|[CMFCToolBarButton::m_bTextBelow](#m_btextbelow)|指定是否在按钮上的图像的下方显示的文本标签。|  
|[CMFCToolBarButton::m_bUserButton](#m_buserbutton)|指定按钮是否具有用户定义的图像。|  
|[CMFCToolBarButton::m_bWholeText](#m_bwholetext)|指定即使无法容纳在边框中的按钮是否显示其完整文本标签。|  
|[CMFCToolBarButton::m_bWrap](#m_bwrap)|指定是否将在下一行上放置分隔符旁边的按钮。|  
|[CMFCToolBarButton::m_bWrapText](#m_bwraptext)|指定是否启用多行文本标签。|  
|[CMFCToolBarButton::m_nID](#m_nid)|按钮的命令 ID。|  
|[CMFCToolBarButton::m_nStyle](#m_nstyle)|按钮样式。|  
|[CMFCToolBarButton::m_strText](#m_strtext)|该按钮的文本标签。|  
  
## <a name="remarks"></a>备注  
 一个`CMFCToolbarButton`对象都是驻留在工具栏的控件。 其行为类似于普通按钮。 可以将图像和文本标签分配给此对象。 工具栏按钮还可以命令 id。 当用户单击工具栏上的按钮时，框架将执行此 ID 指定的命令。  
  
 通常情况下，可以自定义工具栏按钮︰ 用户可以将从一个工具栏按钮拖动到另一个，并将复制、 粘贴、 删除和编辑文本标签和图像。 若要防止用户自定义工具栏，您可以在两种方式之一锁定工具栏。 上述任意一组`bLocked`标记，用于`TRUE`当您调用[CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar)，或通过将各个按钮的命令 ID 添加到受保护的命令的全局列表[CMFCToolBarButton::SetProtectedCommands](#setprotectedcommands)方法。  
  
 `CMFCToolBarButton`对象的应用程序中显示的工具栏图像的全局集合中的图像。 这些集合由在父级工具栏中，维护[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)。 有关详细信息，请参阅[CMFCToolBarImages 类](../../mfc/reference/cmfctoolbarimages-class.md)。  
  
 当用户单击工具栏按钮时，其在父级工具栏处理鼠标消息，并传达给按钮相应的操作。 在父级工具栏按钮有一个有效的命令 ID，如果将发送`WM_COMMAND`与父框架的消息。  
  
 `CMFCToolBarButton`类是类的基类其他工具栏按钮，如[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)， [CMFCToolBarEditBoxButton 类](../../mfc/reference/cmfctoolbareditboxbutton-class.md)，和[CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何配置`CMFCToolBarButton`使用中的各种方法的对象`CMFCToolBarButton`类。 该示例演示了如何能够启用鼠标和键盘输入，设置按钮的图像索引、 设置的边框的按钮，并将按钮可见。 此代码段属于[选项卡控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_TabControl #&1;](../../mfc/reference/codesnippet/cpp/cmfctoolbarbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_TabControl #&2;](../../mfc/reference/codesnippet/cpp/cmfctoolbarbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxtoolbarbutton.h  
  
##  <a name="a-namecanbedroppeda--cmfctoolbarbuttoncanbedropped"></a><a name="canbedropped"></a>CMFCToolBarButton::CanBeDropped  
 指定用户是否可以定位自定义期间的工具栏或菜单上的按钮。  
  
```  
virtual BOOL CanBeDropped(CMFCToolBar* pToolbar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pToolbar`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 此方法返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 默认情况下，工具栏按钮可以删除在每个可自定义 （即未锁定） 工具栏。  
  
 此方法的默认实现返回`TRUE`。 重写此方法并返回`FALSE`如果您想要防止用户重新定位按钮。  
  
##  <a name="a-namecanbestoreda--cmfctoolbarbuttoncanbestored"></a><a name="canbestored"></a>CMFCToolBarButton::CanBeStored  
 确定是否可以存储按钮。  
  
```  
virtual BOOL CanBeStored() const;  
```  
  
### <a name="return-value"></a>返回值  
 此方法返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 框架使用此方法来确定该按钮可以参与拖放操作。  
  
 默认实现返回 `TRUE`。 如果不能作为拖放操作的一部分存储你的按钮，重写此方法。 有关拖放操作的详细信息，请参阅[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
##  <a name="a-namecanbestretcheda--cmfctoolbarbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolBarButton::CanBeStretched  
 指定用户是否可以自定义期间拉伸按钮。  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>返回值  
 此方法返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法由框架用于确定是否可以在自定义模式按钮会被拉伸。  
  
 此方法的默认实现返回`FALSE`。 重写此方法以返回`TRUE`如组合框或滑块的宽度可变的控件。  
  
 有关自定义模式的详细信息，请参阅[CMFCToolBar::SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode)。  
  
##  <a name="a-namecmfctoolbarbuttona--cmfctoolbarbuttoncmfctoolbarbutton"></a><a name="cmfctoolbarbutton"></a>CMFCToolBarButton::CMFCToolBarButton  
 构造并初始化一个 `CMFCToolBarButton` 对象。  
  
```  
CMFCToolBarButton(
    UINT uiID,  
    int iImage,  
    LPCTSTR lpszText=NULL,  
    BOOL bUserButton=FALSE,  
    BOOL bLocked=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiID`  
 按钮的命令 ID。  
  
 [in] `iImage`  
 图像集合中的按钮图像索引。  
  
 [in] `lpszText`  
 该按钮的文本标签。 可以是`NULL`。  
  
 [in] `bUserButton`  
 一个布尔值，确定是否按钮是用户定义。 如果此参数为`TRUE`，是用户定义的按钮。 否则，将从资源加载按钮图像。  
  
 [in] `bLocked`  
 一个布尔值，确定是否可以自定义按钮。 如果此参数为`TRUE`，不能自定义按钮。 否则，可以自定义按钮。  
  
##  <a name="a-namecomparewitha--cmfctoolbarbuttoncomparewith"></a><a name="comparewith"></a>CMFCToolBarButton::CompareWith  
 将此实例与提供`CMFCToolBarButton`对象。  
  
```  
virtual BOOL CompareWith(const CMFCToolBarButton& other) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `other`  
 对要与此实例进行比较的对象引用。  
  
### <a name="return-value"></a>返回值  
 如果所提供的对象等于此实例的值，非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现确定所提供的对象的命令 ID 是否等于此实例的命令 ID。 重写此方法，如果必须执行额外的处理，以确定是否有两个`CMFCToolBarButton`对象是否相等。  
  
##  <a name="a-namecopyfroma--cmfctoolbarbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolBarButton::CopyFrom  
 将另一个工具栏按钮的属性复制到当前按钮。  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `src`  
 源按钮对从中进行复制的引用。  
  
### <a name="remarks"></a>备注  
 调用此方法以将另一个工具栏按钮复制到此工具栏按钮。  
  
##  <a name="a-namecreatefromoledataa--cmfctoolbarbuttoncreatefromoledata"></a><a name="createfromoledata"></a>CMFCToolBarButton::CreateFromOleData  
 创建`CMFCToolBarButton`从所提供的对象`COleDataObject`对象。  
  
```  
static CMFCToolBarButton* __stdcall CreateFromOleData(COleDataObject* pDataObject);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDataObject`  
 源 OLE 数据对象。  
  
### <a name="return-value"></a>返回值  
 创建的 `CMFCToolBarButton` 对象。  
  
### <a name="remarks"></a>备注  
 此方法由框架用于执行各种格式的数据传输。 例如，`CMFCOutlookBarPane::OnDragOver`方法使用此方法来执行拖放操作。  
  
##  <a name="a-nameenablewindowa--cmfctoolbarbuttonenablewindow"></a><a name="enablewindow"></a>CMFCToolBarButton::EnableWindow  
 启用或禁用鼠标和键盘输入。  
  
```  
virtual void EnableWindow(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 此参数设置为`TRUE`若要启用输入，或设置为`FALSE`禁用输入。  
  
### <a name="remarks"></a>备注  
 此方法调用`EnableWindow`函数来启用或禁用输入。 有关详细信息，请参阅[EnableWindow](http://msdn.microsoft.com/library/windows/desktop/ms646291)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameexporttomenubuttona--cmfctoolbarbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolBarButton::ExportToMenuButton  
 复制从工具栏按钮的文本复制到菜单。  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `menuButton`  
 对目标菜单按钮的引用。  
  
### <a name="return-value"></a>返回值  
 此方法返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 框架将调用此方法将从工具栏按钮的文本复制到的菜单按钮。 默认实现将复制该按钮的文本标签。 如果文本标签为空，则此方法复制按钮的工具提示文本。  
  
 此方法的默认实现返回`TRUE`。 重写此方法，如果您想要执行额外的操作时的框架会将一个对象，派生自[CMFCToolbarButton](../../mfc/reference/cmfctoolbarbutton-class.md)到菜单按钮。  
  
##  <a name="a-namegetclipboardformata--cmfctoolbarbuttongetclipboardformat"></a><a name="getclipboardformat"></a>CMFCToolBarButton::GetClipboardFormat  
 检索应用程序的全局剪贴板格式。  
  
```  
static CLIPFORMAT __stdcall GetClipboardFormat();
```  
  
### <a name="return-value"></a>返回值  
 全局`CLIPFORMAT`为应用程序的值。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以检索 OLE 数据传输操作的剪贴板格式。 例如， [CMFCToolBarButton::CreateFromOleData](#createfromoledata)方法使用此方法以将数据复制源 OLE 数据对象。  
  
 此方法可设置全局`CLIPFORMAT`值在首次调用此方法。 此方法对所有后续调用返回此值。  
  
 若要允许拖放操作的应用程序之间出现，请调用[CMFCToolBarButton::SetClipboardFormatName](#setclipboardformatname)方法。  
  
 在 MFC 中的剪贴板的详细信息，请参阅[剪贴板](../../mfc/clipboard.md)。  
  
##  <a name="a-namegethwnda--cmfctoolbarbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBarButton::GetHwnd  
 检索与工具栏按钮关联的窗口句柄。  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>返回值  
 与工具栏按钮关联的窗口句柄或`NULL`工具栏按钮是否没有关联的窗口句柄。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现返回`NULL`。 重写此方法以返回特定控件的窗口句柄。  
  
##  <a name="a-namegetimagea--cmfctoolbarbuttongetimage"></a><a name="getimage"></a>CMFCToolBarButton::GetImage  
 检索按钮的图像索引。  
  
```  
int GetImage() const;  
```  
  
### <a name="return-value"></a>返回值  
 与此按钮关联的图像的索引。  
  
### <a name="remarks"></a>备注  
 如果该按钮具有用户定义的映像 (即，如果`bUserButton`已`TRUE`构造函数中)，因此返回的索引的用户定义的图像集合中指定的图像 (请参阅[CMFCToolBar::GetUserImages](../../mfc/reference/cmfctoolbar-class.md#getuserimages))。 否则，索引从资源文件加载的图像集合中指定的图像 (请参阅[CMFCToolBar::GetImages](../../mfc/reference/cmfctoolbar-class.md#getimages))。 关于资源文件的详细信息，请参阅[使用资源文件](../../windows/working-with-resource-files.md)。  
  
##  <a name="a-namegetinvalidaterecta--cmfctoolbarbuttongetinvalidaterect"></a><a name="getinvalidaterect"></a>CMFCToolBarButton::GetInvalidateRect  
 检索的工作区的按钮必须重绘的区域。  
  
```  
virtual const CRect GetInvalidateRect() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`CRect`对象，它指定必须重绘的区域。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现返回整个客户端区域。 如果您希望不同的区域进行重绘，重写此方法。  
  
##  <a name="a-namegetparentwnda--cmfctoolbarbuttongetparentwnd"></a><a name="getparentwnd"></a>CMFCToolBarButton::GetParentWnd  
 检索父窗口的按钮。  
  
```  
CWnd* GetParentWnd() const;  
```  
  
### <a name="return-value"></a>返回值  
 该按钮的父窗口。  
  
##  <a name="a-namegetprotectedcommandsa--cmfctoolbarbuttongetprotectedcommands"></a><a name="getprotectedcommands"></a>CMFCToolBarButton::GetProtectedCommands  
 检索用户不能自定义的命令的列表。  
  
```  
static const CList<UINT,UINT>& GetProtectedCommands();
```  
  
### <a name="return-value"></a>返回值  
 受保护的命令的列表。  
  
### <a name="remarks"></a>备注  
 在自定义模式下，框架将禁用受保护的工具栏按钮命令。 用户不能执行拖放和编辑已禁用的工具栏按钮上的操作。  
  
 使用[CMFCToolBarButton::SetProtectedCommands](#setprotectedcommands)方法来定义列表的受保护的命令。  
  
##  <a name="a-namegettextsizea--cmfctoolbarbuttongettextsize"></a><a name="gettextsize"></a>CMFCToolBarButton::GetTextSize  
 检索按钮文本的大小。  
  
```  
SIZE GetTextSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`SIZE`对象，其中包含的大小，以像素为单位，按钮文本。  
  
##  <a name="a-namehasfocusa--cmfctoolbarbuttonhasfocus"></a><a name="hasfocus"></a>CMFCToolBarButton::HasFocus  
 确定该按钮是否具有当前输入的焦点。  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果该按钮具有输入的焦点，则为非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果该按钮具有输入的焦点，或者是具有输入的焦点的窗口，一个子节点或子代窗口，此方法的默认实现返回非零值。 您可以重写此函数可自定义此行为。  
  
##  <a name="a-namehavehotbordera--cmfctoolbarbuttonhavehotborder"></a><a name="havehotborder"></a>CMFCToolBarButton::HaveHotBorder  
 确定当用户选择该按钮是否显示按钮的边框。  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>返回值  
 此方法返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以确定是否在用户选择它时，工具栏按钮应显示其边框。  
  
 默认实现返回 `TRUE`。 您可以重写此方法以自定义此行为。  
  
##  <a name="a-nameisdrawimagea--cmfctoolbarbuttonisdrawimage"></a><a name="isdrawimage"></a>CMFCToolBarButton::IsDrawImage  
 确定是否在按钮上显示图像。  
  
```  
BOOL IsDrawImage() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果图像显示在按钮;否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法返回`FALSE`工具栏按钮是否没有关联的图像 ( [CMFCToolBarButton::GetImage](#getimage)返回-1) 或者，如果[CMFCToolBarButton::m_bImage](#m_bimage)设置为`FALSE`。  
  
##  <a name="a-nameisdrawtexta--cmfctoolbarbuttonisdrawtext"></a><a name="isdrawtext"></a>CMFCToolBarButton::IsDrawText  
 确定是否在按钮上显示的文本标签。  
  
```  
BOOL IsDrawText() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果显示的文本标签，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法返回`FALSE`工具栏按钮是否没有关联的文本标签 ( [CMFCToolBarButton::m_strText](#m_strtext)是空的) 或[CMFCToolBarButton::m_bText](#m_btext)设置为`FALSE`。  
  
##  <a name="a-nameisdroppeddowna--cmfctoolbarbuttonisdroppeddown"></a><a name="isdroppeddown"></a>CMFCToolBarButton::IsDroppedDown  
 确定按钮是否显示子菜单。  
  
```  
virtual BOOL IsDroppedDown() const;  
```  
  
### <a name="return-value"></a>返回值  
 此方法返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现返回`FALSE`。 重写此方法以返回`TRUE`如果您的控件显示的子菜单。  
  
##  <a name="a-nameiseditablea--cmfctoolbarbuttoniseditable"></a><a name="iseditable"></a>CMFCToolBarButton::IsEditable  
 确定是否可以自定义按钮。  
  
```  
virtual BOOL IsEditable() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果用户; 可以自定义按钮否则为 0。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以确定用户是否可以通过使用拖放自定义工具栏按钮或编辑操作。  
  
 默认实现返回`FALSE`如果按钮的命令 ID 是标准命令 (您可以通过调用确定这`IsStandardCommand`函数) 或者的命令 ID 是在列表中受到保护的命令。 有关受保护的命令的详细信息，请参阅[CMFCToolBarButton::GetProtectedCommands](#getprotectedcommands)和[CMFCToolBarButton::SetProtectedCommands](#setprotectedcommands)。  
  
 重写此方法以自定义其行为。  
  
##  <a name="a-nameisextrasizea--cmfctoolbarbuttonisextrasize"></a><a name="isextrasize"></a>CMFCToolBarButton::IsExtraSize  
 确定是否可以使用扩展的边框来显示按钮。  
  
```  
virtual BOOL IsExtraSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果工具栏按钮可以显示带有扩展边框; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 多个外观边框的工具栏按钮 （例如，圆形按钮） 使用额外的大小。  
  
 如果用户将此按钮从一个工具栏移到另一个，框架将调用[CMFCToolBarButton::OnChangeParentWnd](#onchangeparentwnd)方法。 [CMFCToolBarButton::OnChangeParentWnd](#onchangeparentwnd)方法将额外大小标志设置为，新的父工具栏 (有关详细信息，请参阅[CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable))。  
  
##  <a name="a-nameisfirstingroupa--cmfctoolbarbuttonisfirstingroup"></a><a name="isfirstingroup"></a>CMFCToolBarButton::IsFirstInGroup  
 确定是否在其按钮组中的第一个位置为按钮。  
  
```  
virtual BOOL IsFirstInGroup() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该按钮是第一个按钮在其按钮组;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法定义*按钮组*为相邻的一组位于同一行上定位，并且受分隔符或工具栏上的边框的按钮。 此方法返回`FALSE`如果工具栏按钮所引用的**自定义**按钮。 有关详细信息**自定义**按钮，请参阅[CMFCToolBar::GetCustomizeButton](../../mfc/reference/cmfctoolbar-class.md#getcustomizebutton)。  
  
 调用[CMFCToolBarButton::IsLastInGroup](#islastingroup)方法，以确定该按钮是否处于其按钮组中的最后一个位置。  
  
##  <a name="a-nameishiddena--cmfctoolbarbuttonishidden"></a><a name="ishidden"></a>CMFCToolBarButton::IsHidden  
 确定按钮处于隐藏状态。  
  
```  
BOOL IsHidden() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果该按钮处于隐藏状态 （不可见）;否则为 0。  
  
### <a name="remarks"></a>备注  
 在父级工具栏拉伸以确定工具栏按钮是否可见时，框架将调用此方法。  
  
 如果您将按钮设置为可通过使用[CMFCToolBarButton::SetVisible](#setvisible)方法中，使用[CMFCToolBarButton::IsVisible](#isvisible)来确定工具栏按钮是否可见。  
  
 默认情况下，所有工具栏按钮都是可见的。 使用[CMFCToolBarButton::Show](#show)方法来隐藏或显示工具栏按钮。  
  
##  <a name="a-nameishorizontala--cmfctoolbarbuttonishorizontal"></a><a name="ishorizontal"></a>CMFCToolBarButton::IsHorizontal  
 确定是否将该按钮处水平工具栏上。  
  
```  
BOOL IsHorizontal() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果工具栏按钮位于水平工具栏; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以确定工具栏按钮的布局。  
  
 此方法返回`m_bHorz`数据成员。 默认值为`m_bHorz`数据成员是`TRUE`; 每次调用将重置[CMFCToolBarButton::OnDraw](#ondraw)方法。  
  
##  <a name="a-nameislastingroupa--cmfctoolbarbuttonislastingroup"></a><a name="islastingroup"></a>CMFCToolBarButton::IsLastInGroup  
 指定的按钮是否在其按钮组中的最后一个位置中。  
  
```  
virtual BOOL IsLastInGroup() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该按钮是最后一个按钮在其按钮组;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法定义*按钮组*相邻组位于同一行上并受分隔符或工具栏上的边框的按钮作为此方法返回`FALSE`如果工具栏按钮已不在父级工具栏或工具栏按钮是指**自定义**按钮。 有关详细信息**自定义**按钮，请参阅[CMFCToolBar::GetCustomizeButton](../../mfc/reference/cmfctoolbar-class.md#getcustomizebutton)。  
  
 调用[CMFCToolBarButton::IsFirstInGroup](#isfirstingroup)方法来确定的按钮是否在其按钮组中的第一个位置。  
  
##  <a name="a-nameislockeda--cmfctoolbarbuttonislocked"></a><a name="islocked"></a>CMFCToolBarButton::IsLocked  
 确定是否已启用锁定的 （非可自定义） 工具栏上的按钮。  
  
```  
BOOL IsLocked() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果该按钮在锁定的工具栏上;否则为 0。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以确定用户是否可以通过使用拖放自定义工具栏按钮或编辑操作。 通过在父级工具栏设置锁定的属性[CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar)方法。 框架将此属性的值传递给构造函数的每个工具栏按钮 ( [CMFCToolbarButton](../../mfc/reference/cmfctoolbarbutton-class.md))，用于插入在父级工具栏。  
  
##  <a name="a-nameisownerofa--cmfctoolbarbuttonisownerof"></a><a name="isownerof"></a>CMFCToolBarButton::IsOwnerOf  
 确定按钮是否提供的窗口句柄的所有者。  
  
```  
virtual BOOL IsOwnerOf(HWND hwnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `hwnd`  
 窗口句柄。  
  
### <a name="return-value"></a>返回值  
 如果该按钮的所有者提供的窗口句柄，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法返回非零 if`hwnd`指的是直接的窗口句柄，或者是与按钮关联的窗口句柄的子级。 如果此方法返回 0`hwnd`是`NULL`。  
  
##  <a name="a-nameisvisiblea--cmfctoolbarbuttonisvisible"></a><a name="isvisible"></a>CMFCToolBarButton::IsVisible  
 确定工具栏按钮是否可见。  
  
```  
BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>返回值  
 工具栏按钮是否可见，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 您可以通过显示或隐藏工具栏按钮使用[CMFCToolBarButton::SetVisible](#setvisible)方法。 调用[CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate)方法在父级工具栏调用后[CMFCToolBarButton::SetVisible](#setvisible)重新计算在父级工具栏的布局。  
  
##  <a name="a-nameiswindowvisiblea--cmfctoolbarbuttoniswindowvisible"></a><a name="iswindowvisible"></a>CMFCToolBarButton::IsWindowVisible  
 确定基础窗口句柄的按钮是否可见。  
  
```  
virtual BOOL IsWindowVisible();
```  
  
### <a name="return-value"></a>返回值  
 如果该按钮的基础窗口句柄是可见的则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法返回非零，如果基础窗口句柄的样式属性包含`WS_VISIBLE`样式。 此方法返回`FALSE`按钮的基础窗口句柄是否`NULL`。  
  
##  <a name="a-namembimagea--cmfctoolbarbuttonmbimage"></a><a name="m_bimage"></a>CMFCToolBarButton::m_bImage  
 指定是否在按钮上显示图像。  
  
```  
BOOL m_bImage;  
```  
  
### <a name="remarks"></a>备注  
 如果此数据成员设置为`TRUE`，框架显示与工具栏按钮关联的图像; 否则该框架将不显示图像。 此成员会影响返回值为[CMFCToolBarButton::m_bImage](#m_bimage)方法。  
  
##  <a name="a-namembtexta--cmfctoolbarbuttonmbtext"></a><a name="m_btext"></a>CMFCToolBarButton::m_bText  
 指定是否在按钮上显示的文本标签。  
  
```  
BOOL m_bText;  
```  
  
### <a name="remarks"></a>备注  
 如果此数据成员设置为`TRUE`，框架显示工具栏按钮的文本标签; 否则该框架将不显示的文本标签。 此成员会影响返回值为[CMFCToolBarButton::m_bText](#m_btext)方法。  
  
##  <a name="a-namembtextbelowa--cmfctoolbarbuttonmbtextbelow"></a><a name="m_btextbelow"></a>CMFCToolBarButton::m_bTextBelow  
 指定是否在按钮上的图像的下方显示的文本标签。  
  
```  
BOOL m_bTextBelow;  
```  
  
### <a name="remarks"></a>备注  
 如果此成员变量设置为`TRUE`，框架显示到该图像下面按钮的文本。 此成员的默认值是`FALSE`。  
  
##  <a name="a-namembuserbuttona--cmfctoolbarbuttonmbuserbutton"></a><a name="m_buserbutton"></a>CMFCToolBarButton::m_bUserButton  
 指定按钮是否具有用户定义的图像  
  
```  
BOOL m_bUserButton;  
```  
  
### <a name="remarks"></a>备注  
 此数据成员设置为`TRUE`该按钮时具有与其关联的用户定义的映像。  
  
##  <a name="a-namembwholetexta--cmfctoolbarbuttonmbwholetext"></a><a name="m_bwholetext"></a>CMFCToolBarButton::m_bWholeText  
 指定即使无法容纳在边框中的按钮是否显示其完整文本标签。  
  
```  
BOOL m_bWholeText;  
```  
  
### <a name="remarks"></a>备注  
 如果此数据成员设置为`TRUE`，框架通过增大按钮显示完整的文本标签。 否则为框架将截断和追加一个省略号 ( **...**) 对文本标签。  
  
##  <a name="a-namembwrapa--cmfctoolbarbuttonmbwrap"></a><a name="m_bwrap"></a>CMFCToolBarButton::m_bWrap  
 指定是否将在下一行上放置分隔符旁边的按钮。  
  
```  
BOOL m_bWrap;  
```  
  
### <a name="remarks"></a>备注  
 框架将此数据成员设置为`TRUE`时工具栏按钮不适合当前行或指定的布局 （例如，特定的工具栏按钮，每个行数）。  
  
 框架在下一行上放置此按钮，如果将此数据成员设置为`TRUE`和工具栏是水平停靠或浮动。  
  
 此数据成员的默认值是`FALSE`。  
  
##  <a name="a-namembwraptexta--cmfctoolbarbuttonmbwraptext"></a><a name="m_bwraptext"></a>CMFCToolBarButton::m_bWrapText  
 指定是否启用多行文本标签。  
  
```  
AFX_IMPORT_DATA static BOOL m_bWrapText;  
```  
  
### <a name="remarks"></a>备注  
 如果此静态成员变量是`TRUE`，该框架允许所有工具栏在工具栏按钮上显示多行文本标签。  
  
 此数据成员的默认值是`FALSE`。  
  
##  <a name="a-namemnida--cmfctoolbarbuttonmnid"></a><a name="m_nid"></a>CMFCToolBarButton::m_nID  
 按钮的命令 ID。  
  
```  
UINT m_nID;  
```  
  
### <a name="remarks"></a>备注  
 命令 ID 为-1 指示按钮是一个分隔符。 所有按钮分隔符都有`TBBS_SEPARATOR`样式。 请参阅[CMFCToolBarButton::m_nStyle](#m_nstyle)按钮样式有关的详细信息。  
  
##  <a name="a-namemnstylea--cmfctoolbarbuttonmnstyle"></a><a name="m_nstyle"></a>CMFCToolBarButton::m_nStyle  
 按钮样式。  
  
```  
UINT m_nStyle;  
```  
  
### <a name="remarks"></a>备注  
 请参阅[工具栏控件样式](../../mfc/reference/toolbar-control-styles.md)有关可用工具栏按钮样式的列表。  
  
##  <a name="a-namemstrtexta--cmfctoolbarbuttonmstrtext"></a><a name="m_strtext"></a>CMFCToolBarButton::m_strText  
 该按钮的文本标签。  
  
```  
CString m_strText;  
```  
  
### <a name="remarks"></a>备注  
 此数据成员包含按钮的文本标签。 文本标签可为空。  
  
##  <a name="a-namenotifycommanda--cmfctoolbarbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarButton::NotifyCommand  
 指定是否处理按钮[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)消息。  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>参数  
 [in] `iNotifyCode`  
 与命令关联通知消息。  
  
### <a name="return-value"></a>返回值  
 此方法返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 框架将调用此方法时将要发送[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)消息发送到父窗口。  
  
 默认情况下，此方法返回`FALSE`。 重写此方法以返回`TRUE`如果想要处理`WM_COMMAND`消息或`FALSE`以指示在父级工具栏应处理消息。  
  
##  <a name="a-nameonaddtocustomizepagea--cmfctoolbarbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarButton::OnAddToCustomizePage  
 当该按钮添加到由框架调用**自定义**对话框。  
  
```  
virtual void OnAddToCustomizePage();
```  
  
### <a name="remarks"></a>备注  
 此方法的默认实现没有任何影响。 重写此方法，如果你想要在该按钮添加到时执行某些操作**自定义**对话框。  
  
##  <a name="a-nameonbeforedraga--cmfctoolbarbuttononbeforedrag"></a><a name="onbeforedrag"></a>CMFCToolBarButton::OnBeforeDrag  
 指定是否可拖动按钮。  
  
```  
virtual BOOL OnBeforeDrag() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可拖动按钮;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在用户开始拖动按钮之前，框架将调用此方法。  
  
 此方法的默认实现返回`TRUE`。 重写此方法以返回`FALSE`禁用拖动按钮。  
  
##  <a name="a-nameonbeforedropa--cmfctoolbarbuttononbeforedrop"></a><a name="onbeforedrop"></a>CMFCToolBarButton::OnBeforeDrop  
 指定用户是否可以放到目标工具栏按钮。  
  
```  
virtual BOOL OnBeforeDrop(CMFCToolBar* pTarget);
```  
  
### <a name="parameters"></a>参数  
 [in] `pTarget`  
 拖放操作的目标。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该按钮可以放置到提供的目标工具栏;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 之前该按钮拖放到工具栏，框架将调用此方法。  
  
 此方法的默认实现返回`TRUE`。 重写此方法以返回`FALSE`禁用指定的目标上拖放操作。  
  
##  <a name="a-nameoncalculatesizea--cmfctoolbarbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFCToolBarButton::OnCalculateSize  
 调用由框架来计算指定的设备上下文和插接状态的按钮的大小。  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 所显示的按钮的设备上下文。  
  
 [in] `sizeDefault`  
 该按钮的默认大小。  
  
 [in] `bHorz`  
 在父级工具栏停靠状态。 此参数是`TRUE`如果工具栏水平停靠或浮动时，或`FALSE`如果垂直停靠工具栏。  
  
### <a name="return-value"></a>返回值  
 一个`SIZE`结构，其中包含按钮，以像素为单位的尺寸。  
  
### <a name="remarks"></a>备注  
 框架调用此方法，以确定指定的设备上下文的工具栏按钮的大小和停靠状态。  
  
 默认实现将考虑的文本和图像的大小 （如果显示）、 文本和图像的位置 （文本下方或图像的右侧） 和工具栏停靠状态。  
  
 如果您想要提供非标准按钮 （例如，一个编辑框按钮） 的大小，重写此方法。  
  
##  <a name="a-nameoncancelmodea--cmfctoolbarbuttononcancelmode"></a><a name="oncancelmode"></a>CMFCToolBarButton::OnCancelMode  
 由框架调用以处理[WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615)消息。  
  
```  
virtual void OnCancelMode();
```  
  
### <a name="remarks"></a>备注  
 此方法的默认实现没有任何影响。 重写此方法，如果你想要处理[WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615)消息。  
  
##  <a name="a-nameonchangeparentwnda--cmfctoolbarbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarButton::OnChangeParentWnd  
 在按钮插入到一个新的工具栏时由框架调用。  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 新的父窗口。  
  
### <a name="remarks"></a>备注  
 按钮时插入到一个工具栏，例如，用户将其从一个工具栏到另一个工具栏。  
  
 此方法的默认实现没有任何影响。  
  
##  <a name="a-nameonclicka--cmfctoolbarbuttononclick"></a><a name="onclick"></a>CMFCToolBarButton::OnClick  
 在用户单击鼠标按钮时由框架调用。  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 工具栏按钮的父窗口。  
  
 [in] `bDelay`  
 `TRUE`如果该消息应该会有一个延迟处理。  
  
### <a name="return-value"></a>返回值  
 此方法返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 在用户单击工具栏上的按钮时，框架将调用此方法。  
  
 默认实现不执行任何操作并返回`FALSE`。 重写此方法以返回一个非零值，如果该按钮处理单击消息。  
  
##  <a name="a-nameonclickupa--cmfctoolbarbuttononclickup"></a><a name="onclickup"></a>CMFCToolBarButton::OnClickUp  
 当用户释放鼠标按钮时由框架调用。  
  
```  
virtual BOOL OnClickUp();
```  
  
### <a name="return-value"></a>返回值  
 此方法返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 当用户释放工具栏按钮时，框架将调用此方法。  
  
 默认实现不执行任何操作并返回`FALSE`。 重写此方法以返回一个非零值，如果该按钮处理单击消息。  
  
##  <a name="a-nameoncontexthelpa--cmfctoolbarbuttononcontexthelp"></a><a name="oncontexthelp"></a>CMFCToolBarButton::OnContextHelp  
 当在父级工具栏处理由框架调用`WM_HELPHITTEST`消息。  
  
```  
virtual BOOL OnContextHelp(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 工具栏按钮的父窗口。  
  
### <a name="return-value"></a>返回值  
 此方法返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现不执行任何操作，并返回`FALSE`。 重写此方法以返回一个非零值，如果该按钮处理此帮助消息。  
  
 有关详细信息`WM_HELPHITTEST`消息，请参见[TN028︰ 上下文相关帮助支持](../../mfc/tn028-context-sensitive-help-support.md)。  
  
##  <a name="a-nameonctlcolora--cmfctoolbarbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarButton::OnCtlColor  
 当在父级工具栏处理由框架调用`WM_CTLCOLOR`消息。  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 所显示的按钮的设备上下文。  
  
 [in] `nCtlColor`  
 特定颜色的通知。  
  
### <a name="return-value"></a>返回值  
 框架将使用绘制按钮的背景画笔对象的句柄。  
  
### <a name="remarks"></a>备注  
 在父级工具栏处理时，框架将调用此方法`WM_CTLCOLOR`包含 Windows 控件的工具栏按钮的消息。 无窗口的工具栏按钮时，框架不调用此方法。  
  
 工具栏框架是在自定义模式和工具栏按钮处于解锁状态时，框架将调用此方法。 有关自定义模式的详细信息，请参阅[CMFCToolBar::SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode)。 有关锁定工具栏按钮的详细信息，请参阅[CMFCToolBarButton::IsLocked](#islocked)。  
  
 默认实现不执行任何操作并返回`NULL`。  
  
##  <a name="a-nameoncustomizemenua--cmfctoolbarbuttononcustomizemenu"></a><a name="oncustomizemenu"></a>CMFCToolBarButton::OnCustomizeMenu  
 允许时应用程序显示在父级工具栏上的快捷菜单上，修改提供菜单按钮。  
  
```  
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMenu`  
 要自定义的菜单。  
  
### <a name="return-value"></a>返回值  
 此方法返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作并返回`FALSE`。 重写此方法并返回一个非零值，如果您想要修改提供菜单上的内容。  
  
##  <a name="a-nameondblclka--cmfctoolbarbuttonondblclk"></a><a name="ondblclk"></a>CMFCToolBarButton::OnDblClk  
 当在父级工具栏处理由框架调用[需知道 WM_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606)消息。  
  
```  
virtual void OnDblClk(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 -   该按钮的父窗口。  
  
### <a name="remarks"></a>备注  
 此方法由`CMFCToolBar::OnLButtonDblClk`方法在父级工具栏在处理时[需知道 WM_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606)消息。  
  
 此方法的默认实现没有任何影响。  
  
##  <a name="a-nameondrawa--cmfctoolbarbuttonondraw"></a><a name="ondraw"></a>CMFCToolBarButton::OnDraw  
 由框架通过使用指定的样式和选项绘制按钮调用。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz=TRUE,  
    BOOL bCustomizeMode=FALSE,  
    BOOL bHighlight=FALSE,  
    BOOL bDrawBorder=TRUE,  
    BOOL bGrayDisabledButtons=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 所显示的按钮的设备上下文。  
  
 [in] `rect`  
 该按钮的边框。  
  
 [in] `pImages`  
 与按钮关联的工具栏图像集合。  
  
 [in] `bHorz`  
 在父级工具栏停靠状态。 此参数是`TRUE`按钮在水平固定和`FALSE`按钮时垂直停靠。  
  
 [in] `bCustomizeMode`  
 指定指示工具栏是否在自定义模式。 此参数是`TRUE`工具栏时自定义模式和`FALSE`工具栏不在自定义模式中时。  
  
 [in] `bHighlight`  
 指定按钮将突出显示。 此参数是`TRUE`时突出显示按钮和`FALSE`按钮将不突出显示。  
  
 [in] `bDrawBorder`  
 指定按钮是否应显示其边框。 此参数是`TRUE`按钮时应显示其边框和`FALSE`按钮时不显示其边框。  
  
 [in] `bGrayDisabledButtons`  
 指定是否带有阴影禁用的按钮或使用已禁用的图像集合。 此参数是`TRUE`禁用的按钮应当显示为灰色和`FALSE`当此方法应使用已禁用的图像集合。  
  
### <a name="remarks"></a>备注  
 重写此方法以自定义工具栏按钮绘图。  
  
##  <a name="a-nameondrawoncustomizelista--cmfctoolbarbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCToolBarButton::OnDrawOnCustomizeList  
 由框架调用以将按钮画入**命令**窗格**自定义**对话框。  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 所显示的按钮的设备上下文。  
  
 [in] `rect`  
 该按钮的边框。  
  
 [in] `bSelected`  
 指定按钮处于选中状态。 如果此参数为`TRUE`，按钮处于选中状态。 如果此参数为`FALSE`，未选中按钮。  
  
### <a name="return-value"></a>返回值  
 以像素为单位指定的设备上下文上的按钮的宽度。  
  
### <a name="remarks"></a>备注  
 自定义对话框中调用此方法 (**命令**选项卡) 按钮时要在自绘列表框中显示本身。  
  
 如果可用，此方法的默认实现将显示按钮的图像和文本标签。 未提供该按钮的文本标签时，该方法将显示工具提示文本。  
  
 重写此方法以执行自定义绘制。  
  
##  <a name="a-nameongetcustomtooltiptexta--cmfctoolbarbuttonongetcustomtooltiptext"></a><a name="ongetcustomtooltiptext"></a>CMFCToolBarButton::OnGetCustomToolTipText  
 由要检索按钮的自定义工具提示文本的框架调用。  
  
```  
virtual BOOL OnGetCustomToolTipText(CString& strToolTip);
```  
  
### <a name="parameters"></a>参数  
 [out] `strToolTip`  
 一个`CString`对象，它接收的自定义工具提示文本。  
  
### <a name="return-value"></a>返回值  
 此方法返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 在显示的工具栏按钮的工具提示时，框架将调用此方法。 如果此方法返回`FALSE`，框架将使用默认工具提示。  
  
 默认实现不执行任何操作并返回`FALSE`。 重写此方法并返回一个非零值可为工具栏按钮提供自定义工具提示文本。  
  
##  <a name="a-nameonglobalfontschangeda--cmfctoolbarbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarButton::OnGlobalFontsChanged  
 当全局字体发生更改时由框架调用。  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>备注  
 此方法的默认实现没有任何影响。 重写此方法以更新用于显示按钮文本的字体。  
  
##  <a name="a-nameonmovea--cmfctoolbarbuttononmove"></a><a name="onmove"></a>CMFCToolBarButton::OnMove  
 当在父级工具栏将由框架调用。  
  
```  
virtual void OnMove();
```  
  
### <a name="remarks"></a>备注  
 此方法的默认实现没有任何影响。 重写此方法以在父级工具栏移动时重新定位按钮。  
  
##  <a name="a-nameonshowa--cmfctoolbarbuttononshow"></a><a name="onshow"></a>CMFCToolBarButton::OnShow  
 由框架调用时该按钮即变为可见或不可见。  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShow`  
 指定的按钮是否可见。 如果此参数为`TRUE`，按钮是否可见。 否则，该按钮不可见。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现没有任何影响。 重写此方法以更新该按钮的可见性。  
  
##  <a name="a-nameonsizea--cmfctoolbarbuttononsize"></a><a name="onsize"></a>CMFCToolBarButton::OnSize  
 在父级工具栏更改其大小或位置和此更改将导致该按钮来更改大小时由框架调用。  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>参数  
 [in] `iSize`  
 新按钮的宽度。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现没有任何影响。 重写此方法以调整了按钮大小的大小或在父级工具栏的位置发生更改时。  
  
##  <a name="a-nameontoolhittesta--cmfctoolbarbuttonontoolhittest"></a><a name="ontoolhittest"></a>CMFCToolBarButton::OnToolHitTest  
 当在父级工具栏必须确定在点是否被按钮的边框时由框架调用。  
  
```  
virtual BOOL OnToolHitTest(
    const CWnd* pWnd,  
    TOOLINFO* pTI);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 该按钮的父窗口。 可以是`NULL`。  
  
 [in] `pTI`  
 一个`TOOLINFO`结构，其中包含有关工具提示控件中的一个工具的信息。  
  
### <a name="return-value"></a>返回值  
 结果`OnMenuButtonToolHitTest`如果按钮可以检索一个指向父框架窗口; 否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果它可以转换为有效帧对象的父窗口，此方法将调用以下方法之一︰  
  
- [CMDIFrameWndEx::OnMenuButtonToolHitTest](../../mfc/reference/cmdiframewndex-class.md#onmenubuttontoolhittest)  
  
- [CFrameWndEx::OnMenuButtonToolHitTest](../../mfc/reference/cframewndex-class.md#onmenubuttontoolhittest)  
  
- [COleIPFrameWndEx::OnMenuButtonToolHitTest](../../mfc/reference/coleipframewndex-class.md#onmenubuttontoolhittest)  
  
##  <a name="a-nameonupdatetooltipa--cmfctoolbarbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarButton::OnUpdateToolTip  
 当在父级工具栏更新其工具提示文本由框架调用。  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 父窗口中。  
  
 [in] `iButtonIndex`  
 父按钮集合中按钮的从零开始索引。  
  
 [in] `wndToolTip`  
 显示的工具提示文本的控件。  
  
 [out] `str`  
 一个`CString`对象，它接收的已更新的工具提示文本。  
  
### <a name="return-value"></a>返回值  
 此方法返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现不执行任何操作，并返回`FALSE`。 重写此方法以返回一个非零值，如果提供了工具提示文本字符串。  
  
##  <a name="a-namepreparedraga--cmfctoolbarbuttonpreparedrag"></a><a name="preparedrag"></a>CMFCToolBarButton::PrepareDrag  
 要执行拖放操作按钮时由框架调用。  
  
```  
virtual BOOL PrepareDrag(COleDataSource& srcItem);
```  
  
### <a name="parameters"></a>参数  
 [in] `srcItem`  
 一个`COleDataSource`对象，它存储有关拖放操作的状态信息。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该操作成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架将调用此方法，以准备工具栏按钮以将其状态储存在提供`COleDataSource`对象。 此方法通过自身序列化为共享文件，然后将传递到该文件来存储其状态[COleDataSource::CacheGlobalData](../../mfc/reference/coledatasource-class.md#cacheglobaldata)方法。 关于工具栏按钮序列化的详细信息，请参阅[CMFCToolBarButton::Serialize](#serialize)。  
  
 此方法不执行任何操作并返回`TRUE`如果不能存储按钮 ( [CMFCToolBarButton::CanBeStored](#canbestored)方法将返回`FALSE`)。 它将返回`FALSE`对象序列化期间发生异常时。  
  
 关于 OLE 拖放操作的详细信息，请参阅[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
##  <a name="a-namerecta--cmfctoolbarbuttonrect"></a><a name="rect"></a>CMFCToolBarButton::Rect  
 检索按钮的边框。  
  
```  
const CRect& Rect() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`CRect`对象，其中包含一个按钮的边框。  
  
##  <a name="a-nameresetimagetodefaulta--cmfctoolbarbuttonresetimagetodefault"></a><a name="resetimagetodefault"></a>CMFCToolBarButton::ResetImageToDefault  
 将设置为默认值是与按钮关联的图像。  
  
```  
virtual void ResetImageToDefault();
```  
  
### <a name="remarks"></a>备注  
 此方法检索默认图像从其父工具栏使用[CMFCToolBar::GetDefaultImage](../../mfc/reference/cmfctoolbar-class.md#getdefaultimage)方法。 如果按钮有没有关联的默认图像，此方法使用按设置其字符串资源根据按钮的文本标签[CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring)方法。 有关字符串资源的详细信息，请参阅[使用资源文件](../../windows/working-with-resource-files.md)。  
  
 如果该按钮具有用户定义的图像，则此方法没有执行任何操作。  
  
##  <a name="a-namesavebarstatea--cmfctoolbarbuttonsavebarstate"></a><a name="savebarstate"></a>CMFCToolBarButton::SaveBarState  
 保存工具栏按钮的状态。  
  
```  
virtual void SaveBarState();
```  
  
### <a name="remarks"></a>备注  
 在创建时，框架将调用此方法`CMFCToolBarButton`对象作为拖放操作的结果。  
  
 此方法的默认实现没有任何影响。 重写此方法以将工具栏按钮的状态保存到外部数据源。  
  
##  <a name="a-nameserializea--cmfctoolbarbuttonserialize"></a><a name="serialize"></a>CMFCToolBarButton::Serialize  
 从存档读取此对象或将其写入存档。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 [in] `ar`  
 `CArchive`从中或向其进行序列化的对象。  
  
### <a name="remarks"></a>备注  
 此方法支持数据传输流程，如剪贴板或拖放操作。 它读取或写入该按钮，例如 ID、 文本标签和图像 ID 的属性，来自或发往所提供`CArchive`对象。  
  
 有关序列化示例，请参阅[序列化︰ 将对象序列化为](../../mfc/serialization-serializing-an-object.md)。  
  
##  <a name="a-namesetaccdataa--cmfctoolbarbuttonsetaccdata"></a><a name="setaccdata"></a>CMFCToolBarButton::SetACCData  
 填充所提供`CAccessibilityData`对象从工具栏按钮可访问性数据。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParent`  
 工具栏按钮的父窗口。  
  
 [in] `data`  
 一个`CAccessibilityData`使用工具栏按钮的可访问性数据填充的对象。  
  
### <a name="return-value"></a>返回值  
 此方法返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 重写此方法以返回`FALSE`如果工具栏按钮不提供辅助功能的数据。  
  
##  <a name="a-namesetclipboardformatnamea--cmfctoolbarbuttonsetclipboardformatname"></a><a name="setclipboardformatname"></a>CMFCToolBarButton::SetClipboardFormatName  
 重命名的全局剪贴板格式。  
  
```  
static void __stdcall SetClipboardFormatName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszName`  
 全局剪贴板格式的新名称。 不能为`NULL`。  
  
### <a name="remarks"></a>备注  
 此方法使才能执行多个应用程序之间的拖放操作。 每个应用程序必须提供相同的剪贴板格式名称。  
  
 必须调用此方法之前框架将调用[CMFCToolBarButton::GetClipboardFormat](#getclipboardformat)。  
  
##  <a name="a-namesetimagea--cmfctoolbarbuttonsetimage"></a><a name="setimage"></a>CMFCToolBarButton::SetImage  
 设置按钮的图像索引。  
  
```  
virtual void SetImage(int iImage);
```  
  
### <a name="parameters"></a>参数  
 [in] `iImage`  
 集合中的工具栏图像的图像的索引。  
  
### <a name="remarks"></a>备注  
 如果工具栏按钮是分隔符，`iImage`指的是分隔符按钮的新宽度。  
  
 如果`iImage`小于零，此方法会禁用绘制图像，并启用该按钮的文本标签的绘图。  
  
##  <a name="a-namesetprotectedcommandsa--cmfctoolbarbuttonsetprotectedcommands"></a><a name="setprotectedcommands"></a>CMFCToolBarButton::SetProtectedCommands  
 设置用户不能自定义的命令的列表。  
  
```  
static void SetProtectedCommands(const CList<UINT,UINT>& lstCmds);
```  
  
### <a name="parameters"></a>参数  
 [in] `lstCmds`  
 受保护的命令的列表。  
  
### <a name="remarks"></a>备注  
 在自定义模式下，框架将禁用受保护的工具栏按钮命令。 用户不能执行拖放和编辑已禁用的工具栏按钮上的操作。  
  
 使用[CMFCToolBarButton::GetProtectedCommands](#getprotectedcommands)方法来检索的列表受保护的命令。  
  
##  <a name="a-namesetradioa--cmfctoolbarbuttonsetradio"></a><a name="setradio"></a>CMFCToolBarButton::SetRadio  
 当一个按钮将其选中的状态更改时由框架调用。  
  
```  
virtual void SetRadio();
```  
  
### <a name="remarks"></a>备注  
 此方法的默认实现没有任何影响。 重写此方法以在该按钮将更改的选中的状态时执行自定义操作。  
  
##  <a name="a-namesetrecta--cmfctoolbarbuttonsetrect"></a><a name="setrect"></a>CMFCToolBarButton::SetRect  
 设置按钮的边框。  
  
```  
void SetRect(const CRect rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `rect`  
 新按钮的边框。  
  
### <a name="remarks"></a>备注  
 此方法调用[CMFCToolBarButton::OnMove](#onmove)方法之后设置的新边框。  
  
##  <a name="a-namesetstylea--cmfctoolbarbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolBarButton::SetStyle  
 设置按钮样式。  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `nStyle`  
 按钮将新样式。  
  
### <a name="remarks"></a>备注  
 默认实现将设置[CMFCToolBarButton::m_nStyle](#m_nstyle)数据成员与`nStyle`。 如果您想要执行其他处理，以处理这些更改在样式中，重写此方法。 请参阅[工具栏控件样式](toolbar-control-styles.md)有关有效的样式标志的列表。  
  
##  <a name="a-namesetvisiblea--cmfctoolbarbuttonsetvisible"></a><a name="setvisible"></a>CMFCToolBarButton::SetVisible  
 指定的按钮是否可见。  
  
```  
void SetVisible(BOOL bShow=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShow`  
 一个布尔值，该值指定是否要显示或隐藏按钮。 如果此参数为`TRUE`，显示按钮。 如果参数是`FALSE`，按钮处于隐藏状态。  
  
### <a name="remarks"></a>备注  
 此函数用于隐藏或显示某个特定工具栏按钮。 调用[CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate)方法后调用此方法。  
  
##  <a name="a-nameshowa--cmfctoolbarbuttonshow"></a><a name="show"></a>CMFCToolBarButton::Show  
 显示或隐藏按钮。  
  
```  
void Show(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShow`  
 一个布尔值，该值指定是否要显示或隐藏按钮。 如果此参数为`TRUE`，显示按钮。 如果参数是`FALSE`，按钮处于隐藏状态。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以调整其在父级工具栏时更新工具栏按钮的可见性。 框架将调用此方法与`bShow`设置为`FALSE`时该按钮不能被装入工具栏的边界内。 框架将调用此方法与`bShow`设置为`TRUE`时在调整大小后按钮再次适合工具栏的边界内。  
  
 使用[CMFCToolBarButton::SetVisible](#setvisible)方法来设置常规按钮的可见性。  
  
 此方法调用[CMFCToolBarButton::OnShow](#onshow)后它将更新按钮的可见性状态的方法。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarImages 类](../../mfc/reference/cmfctoolbarimages-class.md)

