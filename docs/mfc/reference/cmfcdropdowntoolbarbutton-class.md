---
title: "CMFCDropDownToolbarButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownToolbarButton class
- OnCancelMode method
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
caps.latest.revision: 31
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 24398ddb605489bf9677bd493a1bc1f490d583b9
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton 类
一种工具栏按钮，单击时其行为类似于常规按钮。 但是，它将打开一个下拉工具栏 ( [CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)如果用户按下并按住工具栏按钮。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCDropDownToolbarButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|构造 `CMFCDropDownToolbarButton` 对象。|  
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|将另一个工具栏按钮的属性复制到当前按钮。 (重写[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|  
|`CMFCDropDownToolbarButton::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|将打开一个下拉工具栏。|  
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|复制从工具栏按钮的文本复制到菜单。 (重写[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)。)|  
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|检索与按钮关联的下拉列表工具栏。|  
|`CMFCDropDownToolbarButton::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|确定下拉工具栏当前是否已打开。|  
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|确定是否可以使用扩展的边框来显示按钮。 (重写[CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)。)|  
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|调用由框架来计算指定的设备上下文和插接状态的按钮的大小。 (重写[CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|  
|`CMFCDropDownToolbarButton::OnCancelMode`|由框架调用以处理[WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615)消息。 （重写 `CMCToolBarButton::OnCancelMode`。）|  
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|在按钮插入到一个新的工具栏时由框架调用。 (重写[CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)。)|  
|[CMFCDropDownToolbarButton::OnClick](#onclick)|在用户单击鼠标按钮时由框架调用。 (重写[CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。)|  
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|当用户释放鼠标按钮时由框架调用。 (重写[CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)。)|  
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|当在父级工具栏处理由框架调用`WM_HELPHITTEST`消息。 (重写[CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)。)|  
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|当应用程序显示在父级工具栏上的快捷菜单时，请修改提供的菜单。 (重写[CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)。)|  
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|由框架通过使用指定的样式和选项绘制按钮调用。 (重写[CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|  
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|由框架调用以将按钮画入**命令**窗格**自定义**对话框。 (重写[CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|  
|[CMFCDropDownToolbarButton::Serialize](#serialize)|从存档读取此对象或将其写入存档。 (重写[CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|  
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|设置当用户单击按钮时，框架使用的默认命令。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|指定用户必须按住鼠标按钮下拉工具栏出现之前的时间的长度。|  
  
## <a name="remarks"></a>备注  
 一个`CMFCDropDownToolBarButton`与普通按钮不同，因为它有一个小箭头的右下角的按钮。 用户从下拉列表工具栏中选择一个按钮后，框架将显示在顶层工具栏按钮 （带有的右下角的小箭头的按钮） 上其图标。  
  
 有关如何实现下拉工具栏的信息，请参阅[CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)。  
  
 `CMFCDropDownToolBarButton`对象可以导出为[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)对象，并显示为弹出菜单的菜单按钮。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxdropdowntoolbar.h  
  
##  <a name="copyfrom"></a>CMFCDropDownToolbarButton::CopyFrom  
 将另一个工具栏按钮的属性复制到当前按钮。  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `src`  
 源按钮对从中进行复制的引用。  
  
### <a name="remarks"></a>备注  
 调用此方法以将另一个工具栏按钮复制到此工具栏按钮。 `src`类型必须为`CMFCDropDownToolbarButton`。  
  
##  <a name="cmfcdropdowntoolbarbutton"></a>CMFCDropDownToolbarButton::CMFCDropDownToolbarButton  
 构造 `CMFCDropDownToolbarButton` 对象。  
  
```  
CMFCDropDownToolbarButton();

 
CMFCDropDownToolbarButton(
    LPCTSTR lpszName,  
    CMFCDropDownToolBar* pToolBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszName`  
 该按钮的默认文本。  
  
 [in] `pToolBar`  
 一个指向`CMFCDropDownToolBar`当用户按下按钮时显示的对象。  
  
### <a name="remarks"></a>备注  
 第二个重载的构造函数将复制到下拉按钮的第一个按钮从工具栏中，`pToolBar`指定。  
  
 通常情况下，一个下拉工具栏按钮在工具栏中使用从最近使用过按钮的文本，`pToolBar`指定。 它使用指定的文本`lpszName`按钮时将转换为菜单按钮或显示在**命令**的选项卡上**自定义**对话框。 有关详细信息**自定义**对话框中，请参阅[CMFCToolBarsCustomizeDialog 类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCDropDownToolbarButton`类。 此代码段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&31;](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]  
  
##  <a name="dropdowntoolbar"></a>CMFCDropDownToolbarButton::DropDownToolbar  
 将打开一个下拉工具栏。  
  
```  
BOOL DropDownToolbar(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 下拉列表框中，父窗口或`NULL`用于下拉工具栏按钮的父窗口。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 [CMFCDropDownToolbarButton::OnClick](#onclick)方法调用此方法来打开下拉工具栏，当用户按下并按住工具栏按钮。  
  
 此方法通过使用创建下拉工具栏[CMFCDropDownFrame::Create](../../mfc/reference/cmfcdropdownframe-class.md#create)方法。 如果垂直停靠在父级工具栏，此方法将下拉工具栏放到在父级工具栏，具体取决于调整为合适的左侧或右侧一端。 否则，此方法将下拉工具栏放在父级工具栏的下方。  
  
 如果此方法将失败`pWnd`是`NULL`和下拉工具栏按钮没有父窗口。  
  
##  <a name="exporttomenubutton"></a>CMFCDropDownToolbarButton::ExportToMenuButton  
 复制从工具栏按钮的文本复制到菜单。  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `menuButton`  
 对目标菜单按钮的引用。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则为非零；否则为零。  
  
### <a name="remarks"></a>备注  
 此方法会调用基类实现 ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton))，然后将追加到目标菜单按钮包含此按钮在每个工具栏菜单项的弹出菜单。 此方法不将子菜单附加到弹出菜单中。  
  
 如果此方法将失败在父级工具栏`m_pToolBar`，是`NULL`或返回类型的基类实现`FALSE`。  
  
##  <a name="getdropdowntoolbar"></a>CMFCDropDownToolbarButton::GetDropDownToolBar  
 检索与按钮关联的下拉列表工具栏。  
  
```  
CMFCToolBar* GetDropDownToolBar() const;  
```  
  
### <a name="return-value"></a>返回值  
 与按钮关联下拉工具栏。  
  
### <a name="remarks"></a>备注  
 此方法返回`m_pToolBar`数据成员。  
  
##  <a name="isdropdown"></a>CMFCDropDownToolbarButton::IsDropDown  
 确定下拉工具栏当前是否已打开。  
  
```  
BOOL IsDropDown() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果下拉工具栏当前打开，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 该框架使用的打开下拉工具栏[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)方法。 当用户按鼠标左键按钮下拉工具栏的非工作区中，框架将关闭下拉工具栏。  
  
##  <a name="isextrasize"></a>CMFCDropDownToolbarButton::IsExtraSize  
 确定是否可以使用扩展的边框来显示按钮。  
  
```  
virtual BOOL IsExtraSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果工具栏按钮可以显示带有扩展边框; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 有关扩展的边框的详细信息，请参阅[CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)。  
  
##  <a name="m_uishowbardelay"></a>CMFCDropDownToolbarButton::m_uiShowBarDelay  
 指定用户必须按住鼠标按钮下拉工具栏出现之前的时间的长度。  
  
```  
static UINT m_uiShowBarDelay;  
```  
  
### <a name="remarks"></a>备注  
 以毫秒为单位的延迟时间。 默认值为 500。 您可以通过更改此共享的数据成员的值设置另一个延迟。  
  
##  <a name="oncalculatesize"></a>CMFCDropDownToolbarButton::OnCalculateSize  
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
 此方法会扩展的基类实现 ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) 加上该按钮的大小的水平维度的下拉箭头宽度。  
  
##  <a name="onchangeparentwnd"></a>CMFCDropDownToolbarButton::OnChangeParentWnd  
 在按钮插入到一个新的工具栏时由框架调用。  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 新的父窗口。  
  
### <a name="remarks"></a>备注  
 此方法重写基类实现 ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) 通过清除文本标签 ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) 和设置[CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext)和[CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton)数据成员`FALSE`。  
  
##  <a name="onclick"></a>CMFCDropDownToolbarButton::OnClick  
 在用户单击鼠标按钮时由框架调用。  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 工具栏按钮的父窗口。  
  
 [in] `bDelay`  
 `TRUE`如果该消息应该会有一个延迟处理。  
  
### <a name="return-value"></a>返回值  
 如果该按钮处理单击消息时为非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现， [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)，通过更新下拉工具栏的状态。  
  
 当用户单击工具栏上的按钮时，此方法的书签创建计时器等待指定的时间长度[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)数据成员，然后通过打开下拉列表工具栏[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)方法。 此方法关闭下拉工具栏第二次用户单击工具栏上的按钮。  
  
##  <a name="onclickup"></a>CMFCDropDownToolbarButton::OnClickUp  
 当用户释放鼠标按钮时由框架调用。  
  
```  
virtual BOOL OnClickUp();
```  
  
### <a name="return-value"></a>返回值  
 如果该按钮处理单击消息时为非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现， [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)，通过更新下拉工具栏的状态。  
  
 如果处于活动状态，此方法将停止下拉工具栏计时器。 如果已打开，则关闭下拉工具栏。  
  
 有关下拉工具栏和下拉工具栏计时器的详细信息，请参阅[CMFCDropDownToolbarButton::OnClick](#onclick)。  
  
##  <a name="oncontexthelp"></a>CMFCDropDownToolbarButton::OnContextHelp  
 当在父级工具栏处理由框架调用`WM_HELPHITTEST`消息。  
  
```  
virtual BOOL OnContextHelp(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 工具栏按钮的父窗口。  
  
### <a name="return-value"></a>返回值  
 如果该按钮处理帮助消息; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现 ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) 通过调用[CMFCDropDownToolbarButton::OnClick](#onclick)方法`bDelay`设置为`FALSE`。 此方法返回的返回值[CMFCDropDownToolbarButton::OnClick](#onclick)。  
  
 有关详细信息`WM_HELPHITTEST message, see` [TN028︰ 上下文相关帮助支持](../../mfc/tn028-context-sensitive-help-support.md)。  
  
##  <a name="oncustomizemenu"></a>CMFCDropDownToolbarButton::OnCustomizeMenu  
 当应用程序显示在父级工具栏上的快捷菜单时，请修改提供的菜单。  
  
```  
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMenu`  
 要自定义的菜单。  
  
### <a name="return-value"></a>返回值  
 此方法返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现 ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) 通过禁用以下菜单项︰  
  
- **复制按钮图像**  
  
- **按钮外观**  
  
- **图像**  
  
- **文本**  
  
- **图像和文本**  
  
 重写此方法来修改框架在自定义模式下显示的快捷菜单。  
  
##  <a name="ondraw"></a>CMFCDropDownToolbarButton::OnDraw  
 由框架通过使用指定的样式和选项绘制按钮调用。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
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
  
##  <a name="ondrawoncustomizelist"></a>CMFCDropDownToolbarButton::OnDrawOnCustomizeList  
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
 是否选中按钮。 如果此参数为`TRUE`，按钮处于选中状态。 如果此参数为`FALSE`，未选中按钮。  
  
### <a name="return-value"></a>返回值  
 以像素为单位指定的设备上下文上的按钮的宽度。  
  
### <a name="remarks"></a>备注  
 自定义对话框中调用此方法 (**命令**选项卡上) 时所需按钮以将它显示在自绘列表框中。  
  
 此方法会扩展的基类实现 ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) 通过按钮的文本标签更改为按钮的名称 (即，为的值`lpszName`传递给构造函数的参数)。  
  
##  <a name="serialize"></a>CMFCDropDownToolbarButton::Serialize  
 从存档读取此对象或将其写入存档。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 [in] `ar`  
 `CArchive`从中或向其进行序列化的对象。  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现 ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) 通过序列化在父级工具栏的资源 ID。 当加载存档 ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading)返回非零值)，此方法可设置`m_pToolBar`到包含序列化的资源 ID 的工具栏上的数据成员  
  
##  <a name="setdefaultcommand"></a>CMFCDropDownToolbarButton::SetDefaultCommand  
 设置当用户单击按钮时，框架使用的默认命令。  
  
```  
void SetDefaultCommand(UINT uiCmd);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 默认命令 ID。  
  
### <a name="remarks"></a>备注  
 调用此方法以指定用户单击按钮时框架所执行的默认命令。 具有由指定的命令 ID 的项`uiCmd`必须位于父下拉工具栏。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolBar 类](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [演练︰ 将置于工具栏上的控件](../../mfc/walkthrough-putting-controls-on-toolbars.md)




