---
title: "CMFCToolBarEditBoxButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CanBeStretched
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CopyFrom
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetByCmd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContentsAll
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetEditBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetHwnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetInvalidateRect
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::HaveHotBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::IsFlatMode
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::NotifyCommand
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnAddToCustomizePage
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnChangeParentWnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnClick
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnCtlColor
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnGlobalFontsChanged
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnMove
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnShow
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnSize
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnUpdateToolTip
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetFlatMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarEditBoxButton class
- SetACCData method
- OnCalculateSize method
- OnDraw method
- OnDrawOnCustomizeList method
- Serialize method
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
caps.latest.revision: 28
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
ms.openlocfilehash: 7f79c69c9f370f2d79752ed141affac3f97ce716
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton 类
包含一个编辑控件的工具栏按钮 ( [CEdit 类](../../mfc/reference/cedit-class.md))。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCToolBarEditBoxButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|构造 `CMFCToolBarEditBoxButton` 对象。|  
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|指定用户是否可以自定义期间拉伸按钮。 (重写[CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)。)|  
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|将另一个工具栏按钮的属性复制到当前按钮。 (重写[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::CreateEdit](#createedit)|在按钮创建一个新的编辑控件。|  
|`CMFCToolBarEditBoxButton::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|检索第一个`CMFCToolBarEditBoxButton`对象中的应用程序都有指定的命令 id。|  
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|检索具有指定的命令 id。 第一个编辑框工具栏控件的文本|  
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|检索与按钮关联的快捷菜单的资源 ID。|  
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|检索编辑属于编辑框中按钮的边框。|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|返回的指针嵌入在按钮中的编辑控件。|  
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|检索与工具栏按钮关联的窗口句柄。 (重写[CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)。)|  
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|检索的工作区的按钮必须重绘的区域。 (重写[CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)。)|  
|`CMFCToolBarEditBoxButton::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|确定当用户单击按钮时是否显示按钮的边框。 (重写[CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)。)|  
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|确定编辑框按钮是否具有平面样式。|  
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|指定是否处理按钮[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)消息。 (重写[CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)。)|  
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|当该按钮添加到由框架调用**自定义**对话框。 (重写[CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)。)|  
|`CMFCToolBarEditBoxButton::OnCalculateSize`|调用由框架来计算指定的设备上下文和插接状态的按钮的大小。 (重写[CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|  
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|在按钮插入到一个新的工具栏时由框架调用。 (重写[CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)。)|  
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|在用户单击鼠标按钮时由框架调用。 (重写[CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。)|  
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|当在父级工具栏处理由框架调用`WM_CTLCOLOR`消息。 (重写[CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)。)|  
|`CMFCToolBarEditBoxButton::OnDraw`|由框架通过使用指定的样式和选项绘制按钮调用。 (重写[CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|  
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|由框架调用以将按钮画入**命令**窗格**自定义**对话框。 (重写[CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|  
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|当全局字体发生更改时由框架调用。 (重写[CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)。)|  
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|当在父级工具栏将由框架调用。 (重写[CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)。)|  
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|由框架调用时该按钮即变为可见或不可见。 (重写[CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)。)|  
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|在父级工具栏更改其大小或位置和此更改将导致该按钮来更改大小时由框架调用。 (重写[CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)。)|  
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|当在父级工具栏更新其工具提示文本由框架调用。 (重写[CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)。)|  
|`CMFCToolBarEditBoxButton::Serialize`|从存档读取此对象或将其写入存档。 (重写[CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|  
|`CMFCToolBarEditBoxButton::SetACCData`|填充所提供`CAccessibilityData`对象从工具栏按钮可访问性数据。 (重写[CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata)。)|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContents](#setcontents)|设置按钮的编辑控件中的文本。|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|查找编辑控件按钮都有指定的命令 ID，并设置该按钮的编辑控件中的文本。|  
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|指定与按钮关联的快捷菜单的资源 ID。|  
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|指定应用程序中的编辑框按钮的平面样式外观。|  
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetStyle](#setstyle)|指定按钮的样式。 (重写[CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)。)|  
  
## <a name="remarks"></a>备注  
 若要将一个编辑框按钮添加到工具栏，请按照下列步骤︰  
  
 1. 在父级工具栏资源中保留该按钮的虚拟资源 ID。  
  
 2. 构造`CMFCToolBarEditBoxButton`对象。  
  
 3. 在处理该消息处理程序`AFX_WM_RESETTOOLBAR`消息，请将虚拟按钮替换为新的组合框按钮通过使用[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。  
  
 有关详细信息，请参阅[演练︰ 将控件在工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCToolBarEditBoxButton`类。 该示例演示如何指定用户可以自定义期间拉伸按钮，指定当用户单击按钮时显示按钮的边框、 设置文本框控件中的文本、 应用程序中，指定的编辑框按钮的平面样式外观并指定工具栏编辑框控件的样式。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&40;](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 `CMFCToolBarEditBoxButton` 
  
## <a name="requirements"></a>要求  
 **标头︰** afxtoolbareditboxbutton.h  
  
##  <a name="canbestretched"></a>CMFCToolBarEditBoxButton::CanBeStretched  
 指定用户是否可以自定义期间拉伸按钮。  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>返回值  
 此方法返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 默认情况下，框架不允许用户自定义期间拉伸工具栏按钮。 此方法会扩展的基类实现 ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) 通过允许用户自定义期间拉伸编辑框工具栏按钮。  
  
##  <a name="cmfctoolbareditboxbutton"></a>CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton  
 构造[CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)对象。  
  
```  
CMFCToolBarEditBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=ES_AUTOHSCROLL,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiID`  
 指定控件 id。  
  
 [in] `iImage`  
 指定的工具栏图像的从零开始索引。 图像位于[CMFCToolBarImages 类](../../mfc/reference/cmfctoolbarimages-class.md)对象[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)类维护。  
  
 [in] `dwStyle`  
 指定的编辑控件样式。  
  
 [in] `iWidth`  
 指定以像素为单位的编辑控件的宽度。  
  
### <a name="remarks"></a>备注  
 默认构造函数将编辑控件样式设置为以下组合︰  
  
 `WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL`  
  
 该控件的默认宽度为 150 像素。  
  
##  <a name="copyfrom"></a>CMFCToolBarEditBoxButton::CopyFrom  
 将另一个工具栏按钮的属性复制到当前按钮。  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `src`  
 源按钮对从中进行复制的引用。  
  
### <a name="remarks"></a>备注  
 调用此方法以将另一个工具栏按钮复制到此工具栏按钮。 `src`类型必须为`CMFCToolBarEditBoxButton`。  
  
##  <a name="createedit"></a>CMFCToolBarEditBoxButton::CreateEdit  
 在按钮创建一个新的编辑控件。  
  
```  
virtual CEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 `[in] pWndParent`  
 指定的编辑控件的父窗口。 不得为 NULL。  
  
 `[in] rect`  
 指定编辑控件的大小和位置。  
  
### <a name="return-value"></a>返回值  
 指向新创建的编辑控件中;它是`NULL`如果控件的创建和附件失败。  
  
### <a name="remarks"></a>备注  
 您构造`CMFCToolBarEditBoxButton`两个步骤中的对象。 第一次调用构造函数中，，然后调用`CreateEdit,`它创建 Windows 编辑控件并将其附加到`CMFCToolBarEditBoxButton`对象。  
  
##  <a name="getbycmd"></a>CMFCToolBarEditBoxButton::GetByCmd  
 检索第一个`CMFCToolBarEditBoxButton`对象中的应用程序都有指定的命令 id。  
  
```  
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 要检索按钮的命令 ID。  
  
### <a name="return-value"></a>返回值  
 第一个`CMFCToolBarEditBoxButton`中具有指定的命令 ID 的应用程序对象或`NULL`如果不存在任何此类对象。  
  
### <a name="remarks"></a>备注  
 此共享的实用程序方法如由方法[CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)和[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)来设置或获取具有指定的命令 id。 第一个编辑框工具栏控件的文本  
  
##  <a name="getcontentsall"></a>CMFCToolBarEditBoxButton::GetContentsAll  
 检索具有指定的命令 id。 第一个编辑框工具栏控件的文本  
  
```  
static CString __stdcall GetContentsAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 要从中检索内容的按钮命令 ID。  
  
### <a name="return-value"></a>返回值  
 一个`CString`对象，其中包含具有指定的命令 id。 第一个编辑框工具栏控件的文本  
  
### <a name="remarks"></a>备注  
 如果没有，此方法将返回空字符串`CMFCToolBarEditBoxButton`对象具有指定的命令 id。  
  
##  <a name="getcontextmenuid"></a>CMFCToolBarEditBoxButton::GetContextMenuID  
 检索与按钮关联的快捷菜单的资源 ID。  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>返回值  
 程序与按钮或 0，如果该按钮不具有任何关联的快捷方式菜单的快捷菜单资源 ID。  
  
### <a name="remarks"></a>备注  
 框架使用的资源 ID 在用户右键单击该按钮时创建的快捷菜单。  
  
##  <a name="geteditborder"></a>CMFCToolBarEditBoxButton::GetEditBorder  
 检索编辑属于编辑框中按钮的边框。  
  
```  
virtual void GetEditBorder(CRect& rectBorder);
```  
  
### <a name="parameters"></a>参数  
 [out] `rectBorder`  
 对引用`CRect`对象，它接收的边框。  
  
### <a name="remarks"></a>备注  
 此方法检索在工作区坐标的编辑控件的边框。 它扩展在每个方向的矩形的大小增加一个像素。  
  
 [CMFCVisualManager::OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder)方法调用此方法时，它可绘制周围的边框`CMFCToolBarEditBoxButton`对象。  
  
##  <a name="geteditbox"></a>CMFCToolBarEditBoxButton::GetEditBox  
 返回一个指向[CEdit 类](../../mfc/reference/cedit-class.md)嵌入到按钮的控件。  
  
```  
CEdit* GetEditBox() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CEdit 类](../../mfc/reference/cedit-class.md)该按钮包含的控件。 它是`NULL`如果`CEdit`尚未创建控件。  
  
### <a name="remarks"></a>备注  
 您创建`CEdit`控件通过调用[CMFCToolBarEditBoxButton::CreateEdit](#createedit)。  
  
##  <a name="gethwnd"></a>CMFCToolBarEditBoxButton::GetHwnd  
 检索与工具栏按钮关联的窗口句柄。  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>返回值  
 与按钮关联窗口句柄。  
  
### <a name="remarks"></a>备注  
 此方法重写[CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)通过返回一部分编辑控件的编辑框按钮的窗口句柄的方法。  
  
##  <a name="getinvalidaterect"></a>CMFCToolBarEditBoxButton::GetInvalidateRect  
 检索的工作区的按钮必须重绘的区域。  
  
```  
virtual const CRect GetInvalidateRect() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`CRect`对象，它指定必须重绘的区域。  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现， [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)，通过在区域中包括的文本标签的区域。  
  
##  <a name="havehotborder"></a>CMFCToolBarEditBoxButton::HaveHotBorder  
 确定当用户单击按钮时是否显示按钮的边框。  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零值时的按钮显示选择; 时其边框否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现， [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)，通过返回一个非零值，如果控件是否可见。  
  
##  <a name="isflatmode"></a>CMFCToolBarEditBoxButton::IsFlatMode  
 确定编辑框按钮是否具有平面样式。  
  
```  
static BOOL __stdcall IsFlatMode();
```  
  
### <a name="return-value"></a>返回值  
 如果按钮具有平面的样式; 则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 默认情况下，编辑框按钮具有平面样式。 使用[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)方法，以更改您的应用程序的平面样式外观。  
  
##  <a name="notifycommand"></a>CMFCToolBarEditBoxButton::NotifyCommand  
 指定是否处理按钮[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)消息。  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>参数  
 [in] `iNotifyCode`  
 与命令关联通知消息。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该按钮处理`WM_COMMAND`消息，或`FALSE`以指示该消息必须由在父级工具栏进行处理。  
  
### <a name="remarks"></a>备注  
 框架将调用此方法时将要发送[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)消息发送到父窗口。  
  
 此方法会扩展的基类实现 ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) 通过处理[EN_UPDATE](http://msdn.microsoft.com/library/windows/desktop/bb761687)通知。 对于每个具有相同的命令 ID 与此对象的编辑框中，它将设置其文本标签为此对象的文本标签。  
  
##  <a name="onaddtocustomizepage"></a>CMFCToolBarEditBoxButton::OnAddToCustomizePage  
 当该按钮添加到由框架调用**自定义**对话框。  
  
```  
virtual void OnAddToCustomizePage();
```  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现 ( [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) 通过从任何具有相同的命令 ID 与此对象的工具栏中的编辑框控件中复制属性。 如果没有工具栏包含具有相同的命令 ID 与此对象的编辑框控件，则此方法执行任何操作。  
  
 有关详细信息**自定义**对话框中，请参阅[CMFCToolBarsCustomizeDialog 类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarEditBoxButton::OnChangeParentWnd  
 在按钮插入到一个新的工具栏时由框架调用。  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 指向新的父窗口的指针。  
  
### <a name="remarks"></a>备注  
 此方法重写基类实现 ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) 通过重新创建内部`CEdit`对象。  
  
##  <a name="onclick"></a>CMFCToolBarEditBoxButton::OnClick  
 在用户单击鼠标按钮时由框架调用。  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 未使用。  
  
 [in] `bDelay`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 如果该按钮处理单击消息时为非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法重写基类实现 ( [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) 通过返回一个非零值，如果内部`CEdit`对象是可见的。  
  
##  <a name="onctlcolor"></a>CMFCToolBarEditBoxButton::OnCtlColor  
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
 未使用。  
  
### <a name="return-value"></a>返回值  
 指向全局窗口画笔的句柄。  
  
### <a name="remarks"></a>备注  
 此方法重写基类实现 ( [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) 通过分别将提供的设备上下文的文本和背景色设置为全局文本和背景色。  
  
 有关可供您的应用程序的全局选项的详细信息，请参阅[AFX_GLOBAL_DATA 结构](../../mfc/reference/afx-global-data-structure.md)。  
  
##  <a name="onglobalfontschanged"></a>CMFCToolBarEditBoxButton::OnGlobalFontsChanged  
 当全局字体发生更改时由框架调用。  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现 ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) 通过与全局字体更改控件的字体。  
  
 有关可供您的应用程序的全局选项的详细信息，请参阅[AFX_GLOBAL_DATA 结构](../../mfc/reference/afx-global-data-structure.md)。  
  
##  <a name="onmove"></a>CMFCToolBarEditBoxButton::OnMove  
 当在父级工具栏将由框架调用。  
  
```  
virtual void OnMove();
```  
  
### <a name="remarks"></a>备注  
 此方法重写默认类实现 ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) 通过更新内部位置`CEdit`对象  
  
##  <a name="onshow"></a>CMFCToolBarEditBoxButton::OnShow  
 由框架调用时该按钮即变为可见或不可见。  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShow`  
 指定的按钮是否可见。 如果此参数为`TRUE`，按钮是否可见。 否则，该按钮不可见。  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现 ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) 通过显示按钮，如果`bShow`是`TRUE`。 否则，此方法会隐藏按钮。  
  
##  <a name="onsize"></a>CMFCToolBarEditBoxButton::OnSize  
 在父级工具栏更改其大小或位置和此更改将导致该按钮来更改大小时由框架调用。  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>参数  
 [in] `iSize`  
 按钮，以像素为单位的新宽度。  
  
### <a name="remarks"></a>备注  
 此方法重写默认类实现中， [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)，通过更新的大小和位置的内部`CEdit`对象。  
  
##  <a name="onupdatetooltip"></a>CMFCToolBarEditBoxButton::OnUpdateToolTip  
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
 未使用。  
  
 [in] `iButtonIndex`  
 未使用。  
  
 [in] `wndToolTip`  
 显示的工具提示文本的控件。  
  
 [out] `str`  
 一个`CString`对象，它接收的已更新的工具提示文本。  
  
### <a name="return-value"></a>返回值  
 非零，如果此方法将更新的工具提示文本。否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法会扩展的基类实现 ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) 通过显示与按钮的编辑部分相关联的工具提示文本。 如果内部`CEdit`对象是`NULL`或的窗口句柄`CEdit`对象不标识现有的窗口，此方法不执行任何操作并返回`FALSE`。  
  
##  <a name="setcontents"></a>CMFCToolBarEditBoxButton::SetContents  
 设置文本框控件中的文本。  
  
```  
virtual void SetContents(const CString& sContents);
```  
  
### <a name="parameters"></a>参数  
 `[in] sContents`  
 指定要设置的新文本。  
  
##  <a name="setcontentsall"></a>CMFCToolBarEditBoxButton::SetContentsAll  
 查找[CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)具有指定的命令 ID 并将指定的文本设置其文本框内的对象。  
  
```  
static BOOL SetContentsAll(
    UINT uiCmd,  
    const CString& strContents);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 指定该控件将为其更改文本的命令 ID。  
  
 [in] `strContents`  
 指定要设置的新文本。  
  
### <a name="return-value"></a>返回值  
 如果文本已设置，则非零值0`CMFCToolBarEditBoxButton`具有指定的命令 ID 的控件不存在。  
  
##  <a name="setcontextmenuid"></a>CMFCToolBarEditBoxButton::SetContextMenuID  
 指定与按钮关联的快捷菜单的资源 ID。  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 快捷菜单上的资源 ID。  
  
### <a name="remarks"></a>备注  
 框架使用的资源 ID 时在用户右键单击工具栏按钮创建的快捷菜单。  
  
##  <a name="setflatmode"></a>CMFCToolBarEditBoxButton::SetFlatMode  
 指定应用程序中的编辑框按钮的平面样式外观。  
  
```  
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bFlat`  
 编辑框按钮的平面样式。 如果此参数为`TRUE`的平面样式外观，则启用; 否则处于禁用状态的平面样式外观。  
  
### <a name="remarks"></a>备注  
 编辑框按钮的默认平面样式是`TRUE`。 使用[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)方法来检索您的应用程序的平面样式外观。  
  
##  <a name="setstyle"></a>CMFCToolBarEditBoxButton::SetStyle  
 指定工具栏样式的编辑框控件。  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `nStyle`  
 要设置的新样式。  
  
### <a name="remarks"></a>备注  
 此方法可设置[CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle)到`nStyle`它同时还能禁用文本框中，如果应用程序是自定义模式，并且在应用程序不是自定义模式时启用它 (请参阅[CMFCToolBar::SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode)和[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode))。 请参阅[工具栏控件样式](../../mfc/reference/toolbar-control-styles.md)有关有效的样式标志的列表。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CEdit 类](../../mfc/reference/cedit-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [演练︰ 将置于工具栏上的控件](../../mfc/walkthrough-putting-controls-on-toolbars.md)




