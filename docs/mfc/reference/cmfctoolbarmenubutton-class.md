---
title: "CMFCToolBarMenuButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CompareWith
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CopyFrom
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreateFromMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreateMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreatePopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::EnableQuickCustomize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetCommands
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetImageRect
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetPaletteRows
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetPopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::HasButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::HaveHotBorder
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsBorder
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsClickedOnMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsDroppedDown
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsEmptyMenuAllowed
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsExclusive
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsMenuPaletteMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsQuickMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsTearOffMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnAfterCreatePopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnBeforeDrag
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnCalculateSize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnCancelMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnChangeParentWnd
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnClick
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnClickMenuItem
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnContextHelp
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnDraw
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnDrawOnCustomizeList
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OpenPopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::ResetImageToDefault
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SaveBarState
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::Serialize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetACCData
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMenuOnly
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMenuPaletteMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMessageWnd
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetRadio
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetTearOff
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::DrawDocumentIcon
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw
dev_langs: C++
helpviewer_keywords:
- CMFCToolBarMenuButton [MFC], CMFCToolBarMenuButton
- CMFCToolBarMenuButton [MFC], CompareWith
- CMFCToolBarMenuButton [MFC], CopyFrom
- CMFCToolBarMenuButton [MFC], CreateFromMenu
- CMFCToolBarMenuButton [MFC], CreateMenu
- CMFCToolBarMenuButton [MFC], CreatePopupMenu
- CMFCToolBarMenuButton [MFC], EnableQuickCustomize
- CMFCToolBarMenuButton [MFC], GetCommands
- CMFCToolBarMenuButton [MFC], GetImageRect
- CMFCToolBarMenuButton [MFC], GetPaletteRows
- CMFCToolBarMenuButton [MFC], GetPopupMenu
- CMFCToolBarMenuButton [MFC], HasButton
- CMFCToolBarMenuButton [MFC], HaveHotBorder
- CMFCToolBarMenuButton [MFC], IsBorder
- CMFCToolBarMenuButton [MFC], IsClickedOnMenu
- CMFCToolBarMenuButton [MFC], IsDroppedDown
- CMFCToolBarMenuButton [MFC], IsEmptyMenuAllowed
- CMFCToolBarMenuButton [MFC], IsExclusive
- CMFCToolBarMenuButton [MFC], IsMenuPaletteMode
- CMFCToolBarMenuButton [MFC], IsQuickMode
- CMFCToolBarMenuButton [MFC], IsTearOffMenu
- CMFCToolBarMenuButton [MFC], OnAfterCreatePopupMenu
- CMFCToolBarMenuButton [MFC], OnBeforeDrag
- CMFCToolBarMenuButton [MFC], OnCalculateSize
- CMFCToolBarMenuButton [MFC], OnCancelMode
- CMFCToolBarMenuButton [MFC], OnChangeParentWnd
- CMFCToolBarMenuButton [MFC], OnClick
- CMFCToolBarMenuButton [MFC], OnClickMenuItem
- CMFCToolBarMenuButton [MFC], OnContextHelp
- CMFCToolBarMenuButton [MFC], OnDraw
- CMFCToolBarMenuButton [MFC], OnDrawOnCustomizeList
- CMFCToolBarMenuButton [MFC], OpenPopupMenu
- CMFCToolBarMenuButton [MFC], ResetImageToDefault
- CMFCToolBarMenuButton [MFC], SaveBarState
- CMFCToolBarMenuButton [MFC], Serialize
- CMFCToolBarMenuButton [MFC], SetACCData
- CMFCToolBarMenuButton [MFC], SetMenuOnly
- CMFCToolBarMenuButton [MFC], SetMenuPaletteMode
- CMFCToolBarMenuButton [MFC], SetMessageWnd
- CMFCToolBarMenuButton [MFC], SetRadio
- CMFCToolBarMenuButton [MFC], SetTearOff
- CMFCToolBarMenuButton [MFC], DrawDocumentIcon
- CMFCToolBarMenuButton [MFC], m_bAlwaysCallOwnerDraw
ms.assetid: cfa50176-7e4b-4527-9904-86a1b48fc1bc
caps.latest.revision: "31"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f41fc2d55cb5aeb2a8173e9912ddb7c67c582ab9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cmfctoolbarmenubutton-class"></a>CMFCToolBarMenuButton 类
包含一个弹出菜单的工具栏按钮。  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCToolBarMenuButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::CMFCToolBarMenuButton](#cmfctoolbarmenubutton)|构造 `CMFCToolBarMenuButton` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::CompareWith](#comparewith)|将使用提供的此实例进行比较`CMFCToolBarButton`对象。 (重写[CMFCToolBarButton::CompareWith](../../mfc/reference/cmfctoolbarbutton-class.md#comparewith)。)|  
|[Cmfctoolbarmenubutton:: Copyfrom](#copyfrom)|将另一个工具栏按钮的属性复制到当前的按钮。 (重写[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|  
|[CMFCToolBarMenuButton::CreateFromMenu](#createfrommenu)|初始化工具栏菜单从 Windows 菜单句柄。|  
|[CMFCToolBarMenuButton::CreateMenu](#createmenu)|创建一个 Windows 菜单工具栏菜单中的命令组成。 返回的 Windows 菜单的句柄。|  
|[Cmfctoolbarmenubutton:: Createpopupmenu](#createpopupmenu)|创建弹出菜单对象 ( [CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)) 以显示工具栏菜单。|  
|[CMFCToolBarMenuButton::EnableQuickCustomize](#enablequickcustomize)||  
|[CMFCToolBarMenuButton::GetCommands](#getcommands)|工具栏菜单中的命令列表，只读访问。|  
|[CMFCToolBarMenuButton::GetImageRect](#getimagerect)|检索按钮图像的边框。|  
|[CMFCToolBarMenuButton::GetPaletteRows](#getpaletterows)|当该菜单处于调色板模式，请在弹出菜单中返回行的数。|  
|[CMFCToolBarMenuButton::GetPopupMenu](#getpopupmenu)|返回指向与按钮相关联的弹出菜单对象的指针。|  
|[CMFCToolBarMenuButton::HasButton](#hasbutton)||  
|[CMFCToolBarMenuButton::HaveHotBorder](#havehotborder)|确定当用户选择按钮是否显示按钮的边框。 (重写[CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)。)|  
|[CMFCToolBarMenuButton::IsBorder](#isborder)||  
|[CMFCToolBarMenuButton::IsClickedOnMenu](#isclickedonmenu)||  
|[CMFCToolBarMenuButton::IsDroppedDown](#isdroppeddown)|确定是否显示弹出菜单。|  
|[Cmfctoolbarmenubutton:: Isemptymenuallowed](#isemptymenuallowed)|由框架调用以确定用户是否可以从所选的菜单项打开子菜单。|  
|[CMFCToolBarMenuButton::IsExclusive](#isexclusive)|确定按钮是否以独占模式，即，是否弹出菜单保持打开的即使用户将指针移另一个工具栏或按钮。|  
|[CMFCToolBarMenuButton::IsMenuPaletteMode](#ismenupalettemode)|确定弹出菜单是否处于调色板模式。|  
|[CMFCToolBarMenuButton::IsQuickMode](#isquickmode)||  
|[CMFCToolBarMenuButton::IsTearOffMenu](#istearoffmenu)|确定弹出菜单是否具有拖曳栏。|  
|[CMFCToolBarMenuButton::OnAfterCreatePopupMenu](#onaftercreatepopupmenu)||  
|[CMFCToolBarMenuButton::OnBeforeDrag](#onbeforedrag)|指定是否可拖动按钮。 (重写[CMFCToolBarButton::OnBeforeDrag](../../mfc/reference/cmfctoolbarbutton-class.md#onbeforedrag)。)|  
|[CMFCToolBarMenuButton::OnCalculateSize](#oncalculatesize)|由框架调用以计算指定的设备上下文和停靠状态的按钮的大小。 (重写[CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|  
|[CMFCToolBarMenuButton::OnCancelMode](#oncancelmode)|由框架来处理调用[WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615)消息。 (重写[CMFCToolBarButton::OnCancelMode](../../mfc/reference/cmfctoolbarbutton-class.md#oncancelmode)。)|  
|[CMFCToolBarMenuButton::OnChangeParentWnd](#onchangeparentwnd)|按钮插入到一个新工具栏时，由框架调用。 (重写[CMFCToolBarButton::OnChangeParentWnd](cmfctoolbarbutton-class.md#onchangeparentwnd)。)|  
|[CMFCToolBarMenuButton::OnClick](#onclick)|当用户单击鼠标按钮时，由框架调用。 (重写[CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。)|  
|[CMFCToolBarMenuButton::OnClickMenuItem](#onclickmenuitem)|当用户的弹出菜单中选择一项时，由框架调用。|  
|[CMFCToolBarMenuButton::OnContextHelp](#oncontexthelp)|当在父级工具栏处理时由框架调用`WM_HELPHITTEST`消息。 (重写[CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)。)|  
|[CMFCToolBarMenuButton::OnDraw](#ondraw)|由框架调用以绘制按钮通过使用指定的样式和选项。 (重写[CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|  
|[CMFCToolBarMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|由框架绘制按钮调用**命令**窗格**自定义**对话框。 (重写[CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|  
|[CMFCToolBarMenuButton::OpenPopupMenu](#openpopupmenu)|在用户打开的弹出菜单时由框架调用。|  
|[CMFCToolBarMenuButton::ResetImageToDefault](#resetimagetodefault)|将设置为默认值与按钮相关联的映像。 (重写[CMFCToolBarButton::ResetImageToDefault](../../mfc/reference/cmfctoolbarbutton-class.md#resetimagetodefault)。)|  
|[CMFCToolBarMenuButton::SaveBarState](#savebarstate)|保存的工具栏按钮的状态。 (重写[CMFCToolBarButton::SaveBarState](../../mfc/reference/cmfctoolbarbutton-class.md#savebarstate)。)|  
|[CMFCToolBarMenuButton::Serialize](#serialize)|从存档读取该对象或将其写入存档。 (重写[CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|  
|[CMFCToolBarMenuButton::SetACCData](#setaccdata)|填充所提供`CAccessibilityData`与从工具栏按钮的可访问性数据的对象。 (重写[CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata)。)|  
|[CMFCToolBarMenuButton::SetMenuOnly](#setmenuonly)|指定是否可以将按钮添加到工具栏。|  
|[CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode)|指定弹出菜单是否处于调色板模式。|  
|[CMFCToolBarMenuButton::SetMessageWnd](#setmessagewnd)||  
|[CMFCToolBarMenuButton::SetRadio](#setradio)|强制工具栏菜单按钮，以显示一个图标，该值指示已选中。|  
|[CMFCToolBarMenuButton::SetTearOff](#settearoff)|指定拖曳栏的弹出菜单的 ID。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::DrawDocumentIcon](#drawdocumenticon)|在菜单按钮上绘制一个图标。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw](#m_balwayscallownerdraw)|如果`TRUE`，框架将始终调用[CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage)时绘制一个按钮。|  
  
## <a name="remarks"></a>备注  
 A`CMFCToolBarMenuButton`可以显示为菜单、 菜单项具有子菜单、 执行命令或可显示一个菜单的按钮或显示仅菜单按钮。 通过指定参数，如图像、 文本、 菜单句柄，确定的行为和外观的菜单按钮和命令 ID 与构造函数中的按钮的`CMFCToolbarMenuButton::CMFCToolbarMenuButton`。  
  
 自定义的类派生自`CMFCToolbarMenuButton`类必须使用[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏。 [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)应用程序关闭时，宏将生成错误。  
  
## <a name="example"></a>示例  
 下面的示例演示如何配置`CMFCToolBarMenuButton`对象。 代码演示如何指定下拉列表菜单处于调色板模式，并指定当用户拖动从菜单栏中移出的菜单按钮创建的拖曳栏的 ID。 此代码片段属于 [Word Pad 示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad#10](../../mfc/reference/codesnippet/cpp/cmfctoolbarmenubutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxtoolbarmenubutton.h  
  
##  <a name="cmfctoolbarmenubutton"></a>CMFCToolBarMenuButton::CMFCToolBarMenuButton  
 构造 `CMFCToolBarMenuButton` 对象。  
  
```  
CMFCToolBarMenuButton();
CMFCToolBarMenuButton(const CMFCToolBarMenuButton& src);

CMFCToolBarMenuButton(
    UINT uiID,  
    HMENU hMenu,  
    int iImage,  
    LPCTSTR lpszText=NULL,  
    BOOL bUserButton=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `src`  
 现有`CMFCToolBarMenuButton`要复制到此对象`CMFCToolBarMenuButton`对象。  
  
 [in] `uiID`  
 若要在用户单击按钮; 执行的命令 ID或 ( `UINT`)-1 表示不直接执行命令的菜单按钮。  
  
 [in] `hMenu`  
 菜单; 句柄或`NULL`如果按钮不具有一个菜单。  
  
 [in] `iImage`  
 该按钮; 图像的索引如果此按钮不具有一个图标或使用的图标的命令通过指定-1 `uiID`。 索引是相同的每个`CMFCToolBarImages`应用程序中的对象。  
  
 [in] `lpszText`  
 工具栏菜单按钮的文本。  
  
 [in] `bUserButton`  
 `TRUE`如果按钮显示用户定义的图像;`FALSE`如果按钮将显示与指定的命令相关联的预定义的映像`uiID`。  
  
### <a name="remarks"></a>备注  
 如果`uiID`是一个有效命令 ID，按钮执行该命令，当用户单击它。 如果`hMenu`是有效的菜单的句柄，按钮提供了下拉菜单中，当出现在菜单上时，它出现在工具栏或子菜单。 如果这两个`uiID`和`hMenu`有效，该按钮是当用户单击它时将执行的命令部分和使用的向下箭头将下拉列表菜单当用户单击它时部分与拆分按钮。 但是，如果`hMenu`有效，用户将不能单击按钮时按钮插入到菜单执行命令。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCToolBarMenuButton`类。 此代码片段属于 [Word Pad 示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad#9](../../mfc/reference/codesnippet/cpp/cmfctoolbarmenubutton-class_2.cpp)]  
  
##  <a name="comparewith"></a>CMFCToolBarMenuButton::CompareWith  

  
```  
virtual BOOL CompareWith(const CMFCToolBarButton& other) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `other`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="copyfrom"></a>Cmfctoolbarmenubutton:: Copyfrom  

  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `src`  
  
### <a name="remarks"></a>备注  
  
##  <a name="createfrommenu"></a>CMFCToolBarMenuButton::CreateFromMenu  
 初始化工具栏菜单从 Windows 菜单句柄。  
  
```  
virtual void CreateFromMenu(HMENU hMenu);
```  
  
### <a name="parameters"></a>参数  
 [in] `hMenu`  
 菜单句柄。  
  
### <a name="remarks"></a>备注  
 工具栏菜单按钮可显示下拉菜单的子菜单。  
  
 框架调用此方法以初始化菜单的子菜单中的命令。  
  
##  <a name="createmenu"></a>CMFCToolBarMenuButton::CreateMenu  
 创建一个包含工具栏菜单中的命令的菜单。 返回菜单的句柄。  
  
```  
virtual HMENU CreateMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果要菜单 A 处理成功。 `NULL`如果与工具栏菜单按钮关联命令的列表为空。  
  
### <a name="remarks"></a>备注  
 你可以重写此方法在派生类自定义生成菜单的方式。  
  
##  <a name="createpopupmenu"></a>Cmfctoolbarmenubutton:: Createpopupmenu  
 创建`CMFCPopupMenu`对象以显示工具栏菜单。  
  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>返回值  
 指向的指针`CMFCPopupMenu`显示工具栏菜单按钮与关联的下拉列表菜单的对象。  
  
### <a name="remarks"></a>备注  
 由框架准备下拉列表菜单与按钮相关联的显示调用此方法。  
  
 默认实现只需构造并返回一个新`CMFCPopupMenu`对象。 重写此方法，如果你想要使用的派生的类型[CMFCPopupMenu 类](cmfcpopupmenu-class.md)或执行附加的初始化。  
  
##  <a name="drawdocumenticon"></a>CMFCToolBarMenuButton::DrawDocumentIcon  
 在菜单按钮上绘制文档图标。  
  
```  
void DrawDocumentIcon(
    CDC* pDC,  
    const CRect& rectImage,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针。  
  
 [in] `rectImage`  
 图像边界矩形坐标。  
  
 [in] `hIcon`  
 图标句柄。  
  
### <a name="remarks"></a>备注  
 此方法采用一个文档图标，并将其绘制在指定的区域中居中显示的菜单按钮`rectImage`。  
  
##  <a name="enablequickcustomize"></a>CMFCToolBarMenuButton::EnableQuickCustomize  

  
```  
void EnableQuickCustomize();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="hasbutton"></a>CMFCToolBarMenuButton::HasButton  

  
```  
virtual BOOL HasButton() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="havehotborder"></a>CMFCToolBarMenuButton::HaveHotBorder  

  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isborder"></a>CMFCToolBarMenuButton::IsBorder  

  
```  
virtual BOOL IsBorder() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isclickedonmenu"></a>CMFCToolBarMenuButton::IsClickedOnMenu  

  
```  
BOOL IsClickedOnMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isquickmode"></a>CMFCToolBarMenuButton::IsQuickMode  

  
```  
BOOL IsQuickMode();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcommands"></a>CMFCToolBarMenuButton::GetCommands  
 工具栏菜单中的命令列表，只读访问。  
  
```  
const CObList& GetCommands() const;  
```  
  
### <a name="return-value"></a>返回值  
 常量引用到[CObList 类](../../mfc/reference/coblist-class.md)对象，它包含一套[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象。  
  
### <a name="remarks"></a>备注  
 工具栏菜单按钮可以显示子菜单。 你可以提供的构造函数中或在子菜单中的命令的列表[CMFCToolBarMenuButton::CreateFromMenu](#createfrommenu)作为菜单的句柄 ( `HMENU`)。 菜单转换为派生自的对象的列表[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)并存储在内部`CObList`对象。 你可以通过调用此方法访问此列表。  
  
##  <a name="getimagerect"></a>CMFCToolBarMenuButton::GetImageRect  
 检索按钮图像的边框。  
  
```  
void GetImageRect(CRect& rectImage);
```  
  
### <a name="parameters"></a>参数  
 [out] `rectImage`  
 对引用`CRect`接收图像边界矩形的坐标的对象。  
  
##  <a name="getpaletterows"></a>CMFCToolBarMenuButton::GetPaletteRows  
 当该菜单处于调色板模式，请在下拉列表菜单中返回行的数。  
  
```  
int GetPaletteRows() const;  
```  
  
### <a name="return-value"></a>返回值  
 调色板中的行数。  
  
### <a name="remarks"></a>备注  
 当菜单按钮设置为调色板模式中时，菜单项将出现在只有有限数量的行包含多个列。 调用此方法以获取的行数。 你可以启用或禁用调色板模式并指定使用的行数[CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode)。  
  
##  <a name="getpopupmenu"></a>CMFCToolBarMenuButton::GetPopupMenu  
 返回一个指向[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)表示按钮的下拉列表菜单的对象。  
  
```  
CMFCPopupMenu* GetPopupMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)framework 绘制工具栏菜单按钮; 的子菜单时创建的对象`NULL`如果没有子菜单显示。  
  
### <a name="remarks"></a>备注  
 当工具栏菜单按钮显示时的下拉列表菜单时，创建按钮[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象来表示菜单。 调用此方法以获取指向的`CMFCPopupMenu`对象。 因为它是临时的且将变为无效，当用户关闭下拉菜单中，不应存储返回的指针。  
  
##  <a name="isdroppeddown"></a>CMFCToolBarMenuButton::IsDroppedDown  
 指示当前是否显示弹出菜单。  
  
```  
virtual BOOL IsDroppedDown() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果工具栏菜单按钮显示其子菜单;否则为`FALSE`。  
  
##  <a name="isemptymenuallowed"></a>Cmfctoolbarmenubutton:: Isemptymenuallowed  
 指定菜单项是否显示空的子菜单。  
  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果框架在即使子菜单为空; 从当前所选的菜单项打开一个子菜单否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 当用户尝试从当前所选的菜单项打开子菜单时，框架将调用此方法。 如果是空的子菜单和`IsEmptyMenuAllowed`返回`FALSE`，将不会打开子菜单。  
  
 默认实现返回 `FALSE`。 重写此方法以自定义此行为。  
  
##  <a name="isexclusive"></a>CMFCToolBarMenuButton::IsExclusive  
 指示按钮是否以独占模式。  
  
```  
virtual BOOL IsExclusive() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果按钮处理以独占模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 当用户打开一个弹出菜单按钮，然后将鼠标指针移到另一个工具栏或菜单按钮时，弹出菜单关闭除非该按钮以独占模式。  
  
 默认实现始终返回 `FALSE`。 如果你想要打开独占模式，重写此方法在派生类。  
  
##  <a name="ismenupalettemode"></a>CMFCToolBarMenuButton::IsMenuPaletteMode  
 确定下拉列表菜单是否处于调色板模式。  
  
```  
BOOL IsMenuPaletteMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果启用调色板模式，否则`FALSE`。  
  
### <a name="remarks"></a>备注  
 当菜单按钮设置为调色板模式中时，菜单项将出现在只有有限数量的行包含多个列。 调用此方法以获取的行数。 你可以启用或禁用的调色板模式通过调用[CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode)。  
  
##  <a name="istearoffmenu"></a>CMFCToolBarMenuButton::IsTearOffMenu  
 该值指示下拉菜单是否具有拖曳栏。  
  
```  
virtual BOOL IsTearOffMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果工具栏菜单按钮具有拖曳栏;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 若要启用拖曳功能，并设置拖曳栏 ID，调用[CMFCToolBarMenuButton::SetTearOff](#settearoff)。  
  
##  <a name="m_balwayscallownerdraw"></a>CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw  
 指定框架是否始终调用[CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage)时绘制一个按钮。  
  
```  
static BOOL m_bAlwaysCallOwnerDraw;  
```  
  
### <a name="remarks"></a>备注  
 当此成员变量设置为`TRUE`，按钮始终调用[CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage)方法在按钮上显示图像。 当`m_bAlwaysCallOwnerDraw`是`FALSE`，按钮本身绘制的图像，如果预定义映像。 否则，它会调用`OnDrawMenuImage`。  
  
##  <a name="onaftercreatepopupmenu"></a>CMFCToolBarMenuButton::OnAfterCreatePopupMenu  

  
```  
virtual void OnAfterCreatePopupMenu();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="onbeforedrag"></a>CMFCToolBarMenuButton::OnBeforeDrag  

  
```  
virtual BOOL OnBeforeDrag() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="oncalculatesize"></a>CMFCToolBarMenuButton::OnCalculateSize  

  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 [in] `sizeDefault`  
 [in] `bHorz`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="oncancelmode"></a>CMFCToolBarMenuButton::OnCancelMode  

  
```  
virtual void OnCancelMode();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarMenuButton::OnChangeParentWnd  

  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
  
### <a name="remarks"></a>备注  
  
##  <a name="onclick"></a>CMFCToolBarMenuButton::OnClick  

  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 [in] `bDelay`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="onclickmenuitem"></a>CMFCToolBarMenuButton::OnClickMenuItem  
 当用户在下拉菜单中选择一项时，由框架调用。  
  
```  
virtual BOOL OnClickMenuItem();
```  
  
### <a name="return-value"></a>返回值  
 `FALSE`如果框架应继续默认菜单项处理;否则为`TRUE`。 默认实现始终返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 当用户单击菜单项时，框架所执行的与该项关联的命令。  
  
 若要自定义菜单项处理，请重写`OnClickMenuItem`从派生类中`CMFCToolBarMenuButton`类。 你还必须重写[CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu)和替换需要派生的类的实例，并用特殊处理的菜单按钮。  
  
##  <a name="oncontexthelp"></a>CMFCToolBarMenuButton::OnContextHelp  

  
```  
virtual BOOL OnContextHelp(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondraw"></a>CMFCToolBarMenuButton::OnDraw  

  
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
 [in] `rect`  
 [in] `pImages`  
 [in] `bHorz`  
 [in] `bCustomizeMode`  
 [in] `bHighlight`  
 [in] `bDrawBorder`  
 [in] `bGrayDisabledButtons`  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondrawoncustomizelist"></a>CMFCToolBarMenuButton::OnDrawOnCustomizeList  

  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 [in] `rect`  
 [in] `bSelected`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="openpopupmenu"></a>CMFCToolBarMenuButton::OpenPopupMenu  
 在用户打开工具栏菜单按钮的下拉列表菜单时由框架调用。  
  
```  
virtual BOOL OpenPopupMenu(CWnd* pWnd=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 指定接收下拉列表菜单命令的窗口。 它可以是`NULL`只有工具栏菜单按钮有父窗口。  
  
### <a name="return-value"></a>返回值  
 `TRUE`当[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象已创建并打开成功; 否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在用户从工具栏菜单按钮打开下拉列表菜单时，将由框架调用此函数。  
  
##  <a name="resetimagetodefault"></a>CMFCToolBarMenuButton::ResetImageToDefault  

  
```  
virtual void ResetImageToDefault();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="savebarstate"></a>CMFCToolBarMenuButton::SaveBarState  

  
```  
virtual void SaveBarState();
```  
  
### <a name="remarks"></a>备注  
 拖放操作的结果作为创建工具栏按钮时，框架将调用此方法。 此方法调用[CMFCPopupMenu::SaveState](../../mfc/reference/cmfcpopupmenu-class.md#savestate)的顶级弹出菜单上，这会导致重新创建其菜单的弹出菜单的父按钮的方法。  
  
##  <a name="serialize"></a>CMFCToolBarMenuButton::Serialize  

  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 [in] `ar`  
  
### <a name="remarks"></a>备注  
  
##  <a name="setaccdata"></a>CMFCToolBarMenuButton::SetACCData  
 设置功能区元素的可访问性数据。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>参数  
 `pParent`  
 功能区元素的父窗口。  
  
 `data`  
 功能区元素的可访问性数据。  
  
### <a name="return-value"></a>返回值  
 始终返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法将设置功能区元素的可访问性数据，并始终返回 `TRUE`。 重写此方法以设置可访问性数据并返回一个指示成功或失败的值。  
  
##  <a name="setmenuonly"></a>CMFCToolBarMenuButton::SetMenuOnly  
 指定当它具有有效的命令 ID 和子菜单是否为菜单按钮或拆分按钮的绘制按钮。  
  
```  
void SetMenuOnly(BOOL bMenuOnly);
```  
  
### <a name="parameters"></a>参数  
 [in] `bMenuOnly`  
 `TRUE`若要当它具有有效的命令 ID 和子菜单时，显示此按钮为菜单按钮`FALSE`时它具有有效的命令 ID 和子菜单，显示此按钮作为拆分按钮。  
  
### <a name="remarks"></a>备注  
 通常情况下，当工具栏菜单按钮具有子菜单和命令 ID，显示的菜单要向下箭头按钮都有一个主按钮和一个附加的拆分按钮。 如果调用此方法和`bMenuOnly`是`TRUE`，该按钮改为显示要向下箭头按钮中的单个菜单按钮。 当用户单击任何一种模式中的箭头时，将打开子菜单中，并且当用户单击的任何一种模式框架中的按钮的非箭头部分执行的命令。  
  
##  <a name="setmenupalettemode"></a>CMFCToolBarMenuButton::SetMenuPaletteMode  
 指定是否在调色板模式下的下拉列表菜单。  
  
```  
void SetMenuPaletteMode(
    BOOL bMenuPaletteMode=TRUE,  
    int nPaletteRows=1);
```  
  
### <a name="parameters"></a>参数  
 [in] `bMenuPaletteMode`  
 指定是否在调色板模式下的下拉列表菜单。  
  
 [in] `nPaletteRows`  
 调色板中的行数。  
  
### <a name="remarks"></a>备注  
 在调色板模式下，所有菜单项都显示为多列的调色板。 使用指定的行数`nPaletteRows`。  
  
##  <a name="setmessagewnd"></a>CMFCToolBarMenuButton::SetMessageWnd  

  
```  
void SetMessageWnd(CWnd* pWndMessage);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndMessage`  
  
### <a name="remarks"></a>备注  
  
##  <a name="setradio"></a>CMFCToolBarMenuButton::SetRadio  
 设置用于对其进行检查时显示一个单选按钮样式图标的工具栏菜单按钮。  
  
```  
virtual void SetRadio();
```  
  
### <a name="remarks"></a>备注  
 当菜单按钮会绘制时对其进行检查时，它将调用[CMFCVisualManager::OnDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck)要绘制的复选标记图标。 默认情况下，`OnDrawMenuCheck`请求当前视觉管理器绘制一个复选框样式的菜单按钮上的复选标记。 调用此方法后，当前视觉管理器而是在菜单按钮上绘制单选按钮样式复选标记。 无法撤消此更改。  
  
 当调用此方法，并且当前正显示的菜单按钮时，则会刷新。  
  
##  <a name="settearoff"></a>CMFCToolBarMenuButton::SetTearOff  
 指定的下拉列表菜单的拖曳栏的 ID。  
  
```  
virtual void SetTearOff(UINT uiBarID);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiBarID`  
 指定新的分离式栏 id。  
  
### <a name="remarks"></a>备注  
 调用此方法以指定当用户拖动从菜单栏中移出的菜单按钮创建的拖曳栏的 ID。 如果`uiBarID`参数为 0，则用户无法抽出菜单按钮。  
  
 调用[CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)以启用你的应用程序中的拖曳菜单功能。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)